# econ3916-lab10-causal-logic
Lab 10 Submission

# Correlation & Causality: Confounders, Colliders and the Limits of Controls

## Objective
In this lab I show that the same correlation can come from causation, confounding or selection, and that adding a control can either remove bias or create it, depending on the causal structure.

## Methodology
- I simulated three worlds (true causation, pure confounding and pure selection) built so that the correlation between treatment and outcome comes out near 0.65 in each, even though the true effects are 2.0, 0.0 and 0.0.
- I drew a confounder, a collider and a mediator as directed graphs with networkx to make each causal structure explicit.
- I compared regressions with and without each control, to show that controlling for a confounder recovers the true effect while controlling for a collider creates an association between two independent variables.
- I built an M-bias structure, in which a control measured before treatment is a collider of two hidden causes, so adjusting for it still biases the estimate.
- I wrote a small function, `coef_on_d()`, that returns the coefficient on the treatment for any list of controls, and used it to show that also controlling for one of the hidden causes (u1) closes the path again.
- I reproduced the LaLonde (1986) contrast: I compared the estimate from the randomised experiment with the estimate from a comparison group drawn from the CPS, then measured how much of the gap covariate adjustment closes.

## Key Findings
- **Same correlation, different truths:** The three worlds gave correlations of [YOUR VALUE], [YOUR VALUE] and [YOUR VALUE], even though only the first has a real effect (2.0). Correlation alone cannot tell these worlds apart.
- **Colliders create bias:** Controlling for the collider gave a coefficient of [YOUR VALUE] where the truth is 0, producing a large, highly significant association between two independent variables.
- **Pre-treatment does not mean safe:** In the M-bias setup, the pre-treatment control gave [YOUR VALUE]. Once I also controlled for u1, the estimate moved to [YOUR VALUE], because that closes the path the collider had opened.
- **LaLonde:** The experimental estimate was $[YOUR VALUE], the naive CPS comparison gave $[YOUR VALUE], and adding controls gave $[YOUR VALUE], closing [YOUR VALUE]% of the gap. Observed covariates can narrow the gap, but they do not replace randomisation.
- **Main lesson:** Whether a control helps or hurts depends on where it sits in the causal graph, not on whether it is available or measured before treatment.
