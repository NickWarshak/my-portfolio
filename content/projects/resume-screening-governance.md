---
title: "AI Resume Screening"
date: 2026-08-08
draft: false
description: "An AI governance case study: the model that best predicts what recruiters did is not the model that best finds qualified candidates."
tags: ["Python", "scikit-learn", "AI Governance", "Fairness", "SHAP"]
showToc: true
weight: 5
---

[Live Demo](https://nickwarshak.github.io/resume-screening-governance/demo.html) | [Governance Report](https://nickwarshak.github.io/resume-screening-governance/report.html) | [Notebook](https://nickwarshak.github.io/resume-screening-governance/notebook.html) | [Model Card](https://nickwarshak.github.io/resume-screening-governance/model-card.html) | [Source on GitHub](https://github.com/NickWarshak/resume-screening-governance)

### The Finding

I trained two models on the same applicant pool for a software engineering resume screen. The naive one uses 16 features, four of which correlate with protected class. The governed one drops those four and keeps 12.

Score them against what recruiters historically decided, and the naive model wins — AUC 0.911 to 0.865. Score them against who was actually qualified, and it flips — the governed model wins, 0.961 to 0.915.

In production you only ever see the first number. So picking the model that scores best gets you the discriminatory one, while doing everything else by the book.

### Results

| Metric | Naive model | Governed model |
|---|---|---|
| AUC vs. recruiter decisions | 0.911 | 0.865 |
| AUC vs. actual merit | 0.915 | **0.961** |
| Worst impact ratio — sex | 0.612 | **0.967** |
| Worst impact ratio — ethnicity | 0.633 | **0.833** |
| Worst impact ratio — intersection | 0.488 | 0.652 (still fails) |
| Attribution via biased features (SHAP) | 37.7% | 0.0% |
| Red-team cases passed | — | 7 / 7 |

The EEOC's four-fifths rule treats an impact ratio under 0.80 as evidence of adverse impact. The human recruiters in this dataset score 0.607 on sex and 0.583 on ethnicity — worse than either model.

---

### Why This Isn't Just "Trained a Classifier"

* **The ground truth is synthetic, on purpose.** Real hiring data never tells you if a rejected candidate was actually qualified, only whether they were hired — so a fairness audit built on real data can never be proven right or wrong. I generated a synthetic population where true qualification is known and independent of protected class, then injected four bias channels that mirror real ones (referral homophily, an employment-gap penalty, a school-prestige proxy, and a residual penalty modeled on Bertrand & Mullainathan's 2004 callback study). Every disparity the audit finds is provably real.
* **Every model gets scored twice** — against the biased historical label and against synthetic ground truth. That divergence between the two numbers is the whole argument, not a footnote.
* **The live demo is the real model, not a mockup.** It runs the actual trained logistic regression client-side — same standardizer, coefficients, and calibration curve scikit-learn produced. A test pulls the scoring functions straight out of the shipped HTML and runs them under Node against scikit-learn's own output on all 2,400 test applicants. They agree to 1e-13 — floating-point rounding, nothing more. It also computes exact Shapley values in closed form, no `shap` dependency needed for a linear model.
* **The report is gated by code, not just written.** A test suite runs 91 checks that every number and claim in the report text matches the computed pipeline output — not just that the number's right, but that it's actually in the document. I mutation-tested it: corrupting the AUC, the SHAP share, and the sentence disclosing the unresolved fairness gap were each independently caught.
* **A real red-team story.** An early version of the adversarial-input guardrail matched the literal phrase "prompt injection," which meant it penalized legitimate ML/AI safety engineers who described their own work on their resume. I redesigned it to detect instructional framing directed at the system instead of subject matter, and I kept the failing case in the test suite permanently so it can't come back.
* **The model can't reject anyone, by construction.** There's advance, abstain to human review, or low-priority review — no code path returns a rejection. About 23% of applicants land in the abstention band and go to unaided human review instead of being scored at all.

### What I Didn't Fix

The governed model still fails the four-fifths rule at the intersection of sex and ethnicity — Female/Hispanic applicants score 0.652 (95% CI 0.370–0.949, 87% bootstrap probability the breach is real). It passes on sex and ethnicity separately and fails when you look at both together, which is exactly why the law requires intersectional reporting, not just marginal. I tried a few things and none of them were honest fixes, so it's reported instead of hidden.

The data is synthetic. The method is real; a real applicant pool would still need its own audit.

---

### Stack

Python (scikit-learn — `LogisticRegression`, `HistGradientBoostingClassifier`, `CalibratedClassifierCV` with isotonic calibration; pandas, numpy, SHAP, scipy for bootstrap CIs). Vanilla JS for the live demo, plain HTML/CSS for the site — no framework, no build step. Grounded in NYC Local Law 144, the EEOC's Uniform Guidelines, Title VII, Illinois AIVIA, and Colorado SB 24-205.
