# Age–Period–Cohort: the identification problem

In longitudinal studies we typically encounter three temporal variables: **Age** - subjects change over their life course. **Period** - everyone changes at a given moment in calendar time. **Cohort** - subjects born in different years differ from one another. These are related by the identity

$$\text{Cohort} = \text{Period} - \text{Age}$$

Knowing any two fixes the third. Because the three are exactly collinear, their *linear* trends cannot be separated from data alone. It is mathematically impossible.

In this repository I explore the APC identification problem, both the theory and some real world applications from my own field of research.

## What's in here

### [Theory](Theory/)

*The problem, derived three ways.*

Written notes that set out the identification problem in a linear regression, in a survival (Cox) model where age is the underlying time scale, and visually on a Lexis diagram. The document provide some intuition on the APC identification problem, and what we *can* identify.

In this folder you will also find a slide-deck (seven slides) used at work for a small presentation on the subject.

### [Narwhal tusks](Narwhal%20tusks/)

*The problem, in animal ecology.*

Narwhals accumulate chemical constituents throughout their life. Physiology changes with age, which affects both the rate of accumulation and the relative uptake. At the same time, the mineral content of prey and sea water shifts with environmental trends, which is a function of calendar year.

Age and period therefore pull on the same measurement, and disentangling them proves difficult.

## Background reading

- A. Bell (2020), "Age period cohort analysis: a review of what we should and shouldn't do," *Annals of Human Biology* 47(2):208–217.
- A. Bell and K. Jones (2015), "Age, Period and Cohort Processes in Longitudinal and Life Course Analysis: A Multilevel Perspective."
