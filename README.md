# Correlation & Causality: Confounders, Colliders and the Limits of Controls

## Objective

In this lab, I explored why correlation doesn't always mean causation and how controlling for different variables can either reduce or introduce bias when estimating causal effects.

## Methodology

- Simulated three different worlds involving true causation, confounding, and selection bias to compare their correlations and causal effects.
- Used NetworkX to create directed acyclic graphs (DAGs) showing confounders, colliders, and mediators.
- Ran regressions to compare estimates before and after adjusting for confounding variables.
- Tested how controlling for a collider can create a misleading relationship between two independent variables.
- Simulated M-bias to understand why controlling for a variable measured before treatment can still introduce bias.
- Created a `coef_on_d()` function to calculate treatment coefficients using different sets of controls.
- Used NetworkX to identify backdoor paths and find the smallest valid adjustment set.
- Revisited the LaLonde job training experiment and compared the experimental results with an observational comparison group from the CPS.
- Used eight covariates to measure how much regression adjustment reduced the gap between the experimental and observational estimates.

## Key Findings

### Correlation vs. Causation

The three simulated worlds produced correlations near 0.65 even though their true causal effects were 2.0, 0.0, and 0.0. This showed that a strong correlation doesn't necessarily mean one variable causes another because confounding and selection bias can produce similar relationships.

### Confounders and Colliders

The naive regression estimated an effect of 2.476 compared to the true effect of 1.5. After controlling for the confounder U, the estimate decreased to 1.500, matching the true effect.

I also found that conditioning on a collider changed the correlation from -0.017 to -0.596, creating a strong relationship between variables that were originally independent.

### M-Bias

The M-bias simulation showed that controlling for a variable measured before treatment can still introduce bias if that variable is a collider. However, controlling for one of the common causes along the opened path can block that relationship again.

### LaLonde Job Training Experiment

The experimental benchmark showed that the job training program increased earnings by $1,794.

The observational comparison initially estimated an effect of -$8,498, which suggested the opposite conclusion. After controlling for eight covariates, the estimate increased to $699.

This adjustment closed 89% of the gap between the observational and experimental estimates. However, getting closer to the experimental benchmark didn't necessarily prove that the adjustment removed all selection bias.

## Conclusion

This lab helped me understand that statistical significance and strong correlations aren't enough to establish causation. I also learned that adding more control variables doesn't always improve a regression because some variables can introduce bias instead of removing it.

My biggest takeaway is that understanding how variables relate to each other is just as important as running the statistical analysis. A DAG can help identify which variables to control for, but we still need to make sure the graph accurately represents the relationships we're studying.
