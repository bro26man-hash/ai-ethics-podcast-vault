# Open-Source Projects in Algorithmic Fairness & Bias Auditing

A curated list of active open-source projects working on algorithmic fairness, bias detection, and mitigation — tools and frameworks that are shaping how we measure and reduce AI bias.

---

## 1. Trusted-AI / AIF360

| | |
|---|---|
| **GitHub** | [Trusted-AI/AIF360](https://github.com/Trusted-AI/AIF360) |
| **Stars** | ⭐ 2,865 |
| **Language** | Python |
| **Focus** | Fairness metrics, bias mitigation algorithms, debiasing toolkits |

The most established and widely-cited open-source toolkit for AI fairness. AIF360 provides over 70 fairness metrics (demographic parity, equalized odds, predictive parity, etc.) and 11+ debiasing algorithms spanning pre-processing, in-processing, and post-processing. It is used in research, industry, and education worldwide.

**Key debates within the project:** see [DEBATES.md](../blob/main/DEBATES.md) for an ongoing controversy about whether Generalized Entropy Indices are actually *fairness metrics* at all, or just utility functions in disguise.

**Play with it:**
```bash
pip install aif360
```

---

## 2. Fair Code / Fair-Code

| | |
|---|---|
| **GitHub** | [yakew7/Fair-Code](https://github.com/yakew7/Fair-Code) |
| **Stars** | ⭐ 47 |
| **Forks** | 45 |
| **Language** | Python (Jupyter Notebooks) + HTML |
| **License** | MIT |
| **Focus** | Reproducible bias audits across 7 high-stakes domains |

A sharp, practitioner-oriented project that runs the same pipeline across seven real-world audits: Criminal Justice (COMPAS), Hiring, Lending, Healthcare, Welfare Eligibility, Healthcare Readmission, and Tenant Screening. Each audit trains a biased model → measures the fairness gap → engineers a fair model → measures again. Includes 61 plain-language explainers on individual concepts like proxy variables, equalized odds, and the Compas dispute.

**Standout feature:** The Open Dataset Profiler — audits datasets for demographic representation *before* any model is trained, completely client-side in the browser.

**Further reading:** The [Fairness Metrics Conflict explainer](https://github.com/yakew7/Fair-Code/blob/main/explainers/fairness-metric-conflicts.md) is a masterclass in the impossibility of satisfying multiple fairness definitions simultaneously.

---

## 3. Equality AI / EqualityML

| | |
|---|---|
| **GitHub** | [EqualityAI/EqualityML](https://github.com/EqualityAI/EqualityML) |
| **Stars** | ⭐ 35 |
| **Language** | Python (PyTorch/sklearn) + R |
| **License** | Apache 2.0 |
| **Focus** | Evidence-based fairness metric selection & bias mitigation for data scientists |

Built by Equality AI, a public-benefit corporation focused on making fairness accessible to practicing data scientists. EqualityML provides a unified API for fairness metrics and bias mitigation, plus a decision-tree questionnaire that helps you choose the right fairness metric for your use case. Supports both pre-processing and in-processing mitigation.

**Let's talk:** A community is mentioned — if you're using this tool, consider joining the [Equality AI Slack](https://equalityai.com/slack) to discuss metric selection and mitigation strategies in practice.

---

## How to Add a Project to This List

1. Find an active, open-source project related to algorithmic fairness or bias auditing
2. Verify it has recent activity (commits within the last 6 months, open issues/discussions)
3. Add a card to this file following the template above
4. Open a pull request with your addition

---

*Last updated: September 2026*
