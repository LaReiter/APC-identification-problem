# Age–Period–Cohort: the identification problem

Three time scales shape almost any longitudinal measurement. **Age** — individuals change over their life course. **Period** — everyone changes at a given moment in calendar time. **Cohort** — people born in different years differ from one another.

They are bound by a single identity:

$$\text{Cohort} = \text{Period} - \text{Age}$$

Knowing any two fixes the third. Because the three are exactly collinear, their *linear* trends cannot be separated from data alone. No sample size and no amount of model sophistication resolves this — only an explicit, theory-based assumption does.

This repository explores what that costs us: first the theory, then what it does to a real measurement problem.

## What's in here

### [Theory](Theory/)

*The problem, derived three ways.*

Written notes that set out the identification problem in a linear regression, in a Cox model where age is the underlying time scale, and visually on a Lexis diagram. They close with what does remain estimable — curvature, discrete jumps, and certain sums of the linear terms — and with why the popular "solutions" tend to hide an assumption rather than remove one.

The same material is also available as a self-contained slide deck.

### [Narwhal tusks](Narwhal%20tusks/)

*The problem, in the field.*

Narwhals accumulate chemical constituents throughout their life. Physiology changes with age, which affects both the rate of accumulation and the relative uptake. At the same time, the mineral content of prey and sea water shifts with environmental trends — that is, as a function of calendar year.

Age and period therefore pull on the same measurement, and disentangling them proves hard.

## Background reading

- A. Bell (2020), "Age period cohort analysis: a review of what we should and shouldn't do," *Annals of Human Biology* 47(2):208–217.
- A. Bell and K. Jones (2015), "Age, Period and Cohort Processes in Longitudinal and Life Course Analysis: A Multilevel Perspective."
