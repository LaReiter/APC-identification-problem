# Age, period and cohort

### The ubiquitous identification problem

*by Lars Nørtoft Reiter*

Is Generation Z[^genz] more susceptible to psychiatric illness than, say, Millennials[^mill]?

If such a contrast exists, we would deem it a cohort effect: something related to the birth year of the individual(s). There are two other related effects, namely age and period (calendar year).

Age effects are due to changes over the life course of the individual. These could be changes in physiology, personality or political views. Period effects are due to changes in particular calendar years, for example due to recessions, pandemics or other phenomena.

In a longitudinal study each subject carries three temporal coordinates: age $A$, period $P$ (the calendar year), and birth cohort $C$ (year of birth). These are perfectly collinear as

$$C = P - A .$$

Knowing any two determines the third. This single fact is the root of what is known as the **Age–Period–Cohort (APC) identification problem**.

## The identification problem in a simple regression

To illustrate the identification problem, consider a linear regression

$$\text{Observation} = \beta_A \text{Age} + \beta_P \text{Period} + \beta_C \text{Cohort} + \text{Error}$$

Let us now shift these parameters in a very specific way by introducing a constant $k$:

$$\beta_A' = \beta_A + k \qquad \beta_P' = \beta_P - k \qquad \beta_C' = \beta_C + k$$

If we do the algebra, we see that this new set of parameters yields a regression that is observationally equivalent to the one with the original set of parameters:

$$
\begin{aligned}
\text{Observation} &= \beta_A' \text{Age} + \beta_P' \text{Period} + \beta_C' \text{Cohort} + \text{Error} \\
&= \beta_A \text{Age} + \beta_P \text{Period} + \beta_C \text{Cohort} + k (\text{Age} - \text{Period} + \text{Cohort}) + \text{Error} \\
&= \beta_A \text{Age} + \beta_P \text{Period} + \beta_C \text{Cohort} + \text{Error}
\end{aligned}
$$

where the last equality holds because the identity $C = P - A$ implies that the term $k (\text{Age} - \text{Period} + \text{Cohort})$ is identically zero.

> **Example**
>
> Assume true parameters $\beta_A = \beta_P = \beta_C = 1$ and define the constant $k = -1$. We then find
>
> **True model:**  $\text{Observation} = 1 \cdot \text{Age} + 1 \cdot \text{Period} + 1 \cdot \text{Cohort} + \text{Error}$
>
> **Fitted model:**  $\text{Observation} = 2 \cdot \text{Period} + \text{Error}$
>
> Our fitted model shows no effect of age and no effect of cohort, in contrast to the true model in which both are present. In a practical setting this means we would conclude that the observed quantity is unrelated to the individual's life stage and unrelated to their birth year, and attribute all of it to the calendar year. We then risk putting our full attention on contemporary exterior causes, possibly leading to misguided policies or interventions.

## The identification problem in survival analysis

In epidemiology we typically settle on some underlying time scale. This could be age $A$. In a Cox regression model, the age enters nonparametrically through the baseline hazard, whereas period $P$ and cohort $C$ become part of the parametric term

$$\lambda(A ; P, C) = \lambda_0(A) \exp\big( \beta_P P + \beta_C C \big)$$

### How the non-identifiability emerges

Substitute the identity $C = P - A$ into the linear predictor

$$\beta_P P + \beta_C C = \beta_P P + \beta_C (P - A) = \underbrace{(\beta_P + \beta_C)}_{\gamma} P - \beta_C A$$

The term $-\beta_C A$ is a function of age alone, so it can be absorbed into the baseline

$$\tilde\lambda_0(A) = \lambda_0(A) \exp(-\beta_C A)$$

such that the model now becomes

$$\lambda(A ; P) = \tilde\lambda_0(A) \exp\big( \gamma P \big) \qquad \gamma = \beta_P + \beta_C .$$

In other words, the data can inform us only about the baseline shape $\tilde\lambda_0(A)$ and the coefficient $\gamma$, which is sometimes called the *cohort replacement effect*.

## What can we identify?

The APC identification problem concerns the *linear* trends only. It does not mean the data are uninformative about age, period, and cohort.

Once these effects are allowed to enter non-linearly (say as factors or splines), the curvature of each component, that is, its deviation from linearity (its second differences), is identifiable.

The division of the parameter space into an inestimable pair of linear trends on one side, and estimable curvatures on the other, is an old conclusion of Holford (1983) and Clayton and Schifflers (1987).[^holford]

In the linear case, we are unable to provide point estimates without assumptions on the age, period and cohort effects.

What we can estimate is instead a line of solutions, described by the shifted parameters $(\beta_A', \beta_P', \beta_C')$ above. In addition, using those same shifted parameters, we can estimate combined effects:

$$
\begin{aligned}
\delta &:= \beta_A' + \beta_P' = \beta_A + \beta_P \qquad \textit{(individual change effect)} \\
\gamma &:= \beta_C' + \beta_P' = \beta_C + \beta_P \qquad \textit{(cohort replacement effect)}
\end{aligned}
$$

Here $\delta$ describes the total change of an individual from aging and from changes due to calendar year, whereas $\gamma$ describes the total change of an individual from the person's birth year and from changes due to calendar year.

A third combination follows immediately from the two above,

$$\delta - \gamma = \beta_A - \beta_C \qquad \textit{(cross-sectional effect)}$$

## Fancy methods and Lexis diagrams

Separating age, period and cohort effects from data alone is mathematically impossible. To do so demands assumptions, based on prior knowledge.

Still, many have attempted this impossible quest.

One of the examples provided in Bell (2020)[^bell] is the hierarchical APC (HAPC) model, which treats period and cohort as cross-classified random effects, whereas age enters as a fixed effect. It turns out that the model shrinks the linear cohort effect towards zero, effectively masking an underlying assumption about the APC effects.

Lexis diagrams are also commonly used, and while these can be extremely useful visual tools, it is important to know in which ways. A Lexis diagram places calendar time on the horizontal axis and age on the vertical, so each individual is a line segment at $45$ degrees. Plotting rates on this plane shows all three time scales at once, since a cell fixes age, period and, by the identity $C = P - A$, birth cohort.

Consider the figure below, where the black diagonals are lifelines and the dots mark death. The purple horizontal band (C) shows rates around age $20$ elevated relative to adjacent ages, in every calendar year, illustrating an *age effect*. The red vertical band (A) shows rates around $1945$ elevated relative to adjacent years, at every age, illustrating a *period effect*. The green diagonal band (B) shows rates elevated relative to adjacent birth cohorts, wherever those cohorts fall, illustrating a *birth cohort effect*.

![Schematic Lexis diagram with calendar year on the horizontal axis and age on the vertical axis. Black diagonal lifelines run at 45 degrees, ending in dots that mark death. A vertical red band at 1945 marks a period effect, a diagonal green band marks a birth cohort effect, and a horizontal purple band at age 20 marks an age effect.](graphics/lexis-diagram.png)

*A schematic Lexis diagram. Black diagonals are individual lifelines, with dots marking death. Band C is horizontal and marks an age effect, band A is vertical and marks a period effect, and band B is diagonal and marks a birth cohort effect.*

What is important to note is that we can identify deviations, that is, groups that stand out from their neighbours, but we cannot split the linear drift into period and cohort components. Formally, we can identify second differences, that is, curvature, whereas of the first differences we recover only their sum $\gamma$; the separate period and cohort slopes remain out of reach, owing to the identity $C = P - A$.

So what the Lexis diagram shows us is the estimable non-linear part. A hump over a few calendar years or a ridge along one diagonal cannot be produced by effects on the other two axes. But the background slope those features sit on is not attributable, since steadily worsening cohorts masked by faster period improvement give the same surface as identical cohorts with period-driven improvement. An absence of diagonal structure therefore rules out cohort deviations, but not a cohort trend.

## The slides

During a journal club at work, I also gave a short talk on the APC identification problem, built using [Quarto](https://quarto.org). 

| File | What it is |
| --- | --- |
| [`APC.qmd`](APC.qmd) | Source of the deck. Render with `quarto render APC.qmd`, or preview live with `quarto preview APC.qmd`. |
| [`APC.html`](APC.html) | The rendered deck. Needs `APC_files/` and `graphics/` alongside it. |
| [`custom.scss`](custom.scss) | Theme overrides used by the deck. |

The deck is made up of seven slides:

1. The three effects and what they look like in the world.
2. The identity $\text{Age} = \text{Period} - \text{Cohort}$.
3. The linear model and the same worked example used above.
4. The geometry of the line of solutions.
5. The problem visualized in cross-sectional, single-cohort and combined designs.
6. Proposed "solutions" without assumptions: the line of solutions itself, and hierarchical APC.
7. Proposed "solutions" with assumptions: categorical APC, and substituting the real mechanism for one of the three axes.

> **Note on viewing:** GitHub shows `.html` files as source rather than rendering them, you might need to open `APC.html` locally.

[^genz]: Born between 1997 and 2012.
[^mill]: Born between 1981 and 1996.
[^holford]: T. R. Holford (1983), "The estimation of age, period and cohort effects for vital rates," *Biometrics* 39(2):311–324; D. Clayton and E. Schifflers (1987), "Models for temporal variation in cancer rates. II: age–period–cohort models," *Statistics in Medicine* 6(4):469–481.
[^bell]: A. Bell (2020), "Age period cohort analysis: a review of what we should and shouldn't do," *Annals of Human Biology* 47(2):208–217.
