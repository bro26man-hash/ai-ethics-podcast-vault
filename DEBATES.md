# Ongoing Debates in Algorithmic Fairness

A collection of real, unresolved controversies from the open-source AI fairness community — framed for podcast discussion and listener debate.

---

## Debate #1: Is a Utility-Based Index Actually a Fairness Metric?

**Source:** [Trusted-AI/AIF360 PR #214](https://github.com/Trusted-AI/AIF360/pull/214) — "Add generic benefit function for inequality indices" (Open, 9 comments, 2020-2023)

**The core question:**
Can a metric that measures prediction accuracy across groups ever count as a *fairness* metric — or is it really just a utility function wearing a fairness label?

**The background:**
AIF360's sklearn API categorizes Generalized Entropy Indices (GEI) alongside consistency scores (from Dwork et al.'s "Fairness Through Awareness" definition) under "individual fairness metrics." A contributor named `leenamurgai` came along and challenged that categorization — with a mathematical proof.

**The argument (leenamurgai → AIF360 maintainers, Nov 2022):**

- GEI can be *rewritten* as a function of just two things: model accuracy (λ) and mean benefit (μ).
- When α=2, minimizing GEI is equivalent to minimizing mean squared error — i.e., improving accuracy.
- When α=0, minimizing GEI is equivalent to minimizing cross-entropy loss — again, a utility optimization.
- Therefore, GEI is not a measure of *individual fairness* (which, per Dwork et al. 2011, asks "are similar people treated similarly?" using a similarity metric defined *apart from* the data). GEI is a measure of utility.
- The AIF360 paper that claims GEI measures individual fairness may actually be demonstrating the classic trade-off between *utility and fairness* — but calling it "utility vs. fairness" would be far more honest.
- The mainlanding consequences: if GEI is a utility metric, then its "trade-off with fairness" is really just the well-known utility-fairness trade-off, and the categorization as an individual fairness metric is misleading.

**The counter-response (hoffmansc → leenamurgai, Nov-Dec 2022):**

- The math checks out, but GEI might still be a fairness metric in a *different* sense — one based on distributional equality rather than Dwork et al.'s individual-similarity definition.
- The suggestion: categorize GEI as "distributional fairness" and give users a clear note explaining the distinction.
- On the original PR: name the benefit-function cases more transparently (e.g., "accuracy," "luck") instead of using opaque parameter names.

**The deeper question that IMF (and the broader field) never fully resolved:**

When we say a fairness metric "satisfies" or "violates" a criterion, whose baseline are we measuring against? In the COMPAS system, Black defendants recidivate at higher base rates in the training data — but that base rate is itself a product of over-policing. A model that achieves "predictive parity" against this corrupted baseline is calibrating its injustice. Which comes first: the metric, or the data pipeline that defines what "ground truth" even means?

**Why this matters for your podcast:**

This is not just a taxonomy argument. If AI fairness tools count utility as fairness, they can tell a company "our model is fair" precisely when it's optimizing outcomes that harm the most vulnerable — because the utility function doesn't notice the harm, it just notices a lower accuracy score. The metric itself becomes a shield against accountability.

**The stakeholders at the table:**
- Researchers writing and deploying Fairness ML tooling
- Regulators and courts invoking different fairness definitions
- The people whose lives are shaped by automated decisions
- The companies building and selling these systems

---

## Honorable Mention: The Impossibility of Satisfying All Three Metrics

**Source:** [Fair-Code explainer: Why Fairness Metrics Conflict](https://github.com/yakew7/Fair-Code/blob/main/explainers/fairness-metric-conflicts.md) (inspired by Chouldechova 2017 & Kleinberg et al. 2016)

When base rates differ across groups (and they always do in practice), you cannot simultaneously satisfy:

| Fairness criterion | What it demands | Real-world cost when it fails |
|---|---|---|
| **Demographic Parity** | Equal positive prediction rates | Groups with higher true positive rates may be under-predicted |
| **Equalized Odds** | Equal error rates (TPR + FPR) | Predictive accuracy per group may be sacrificed |
| **Predictive Parity** | Equal reliability of predictions | Groups with lower base rates face higher false positive rates |

The ProPublica vs. Northpointe COMPAS debate is the public case study: ProPublica looked at false positive rates and found racial disparity; Northpointe pointed to predictive parity and said "we're closer than you think." Both were mathematically correct. They were just measuring different things — and each measurement led to a different policy prescription.

**The follow-up question:** Whose interests does each metric serve — and who decides which group bears the cost of getting it wrong?

---

*Contributions welcome. Found an interesting debate thread? Add it using the template above — open an issue to propose it.*
