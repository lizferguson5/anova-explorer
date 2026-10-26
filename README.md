# ANOVA vs T-Test Explorer

An interactive, browser-based tool for biostatistics students to build a deep visual understanding of one-way ANOVA and the independent t-test — how they partition variance, when to use each, and what the F and t distributions actually mean.

🔗 **[ANOVA App](https://lizferguson5.github.io/anova-explorer/)**

---

## Overview

Students often learn ANOVA as a formula to apply rather than a concept to understand. This tool makes the logic concrete: you can see the between-group signal and within-group noise drawn directly on the data, watch the F-ratio and p-value respond in real time as you move a slider, and compare the t-test and ANOVA side by side to understand when — and why — they are mathematically identical.

Everything is computed live in the browser from randomly generated group data. No software installation required.

---

## Intended Audience

Undergraduate and graduate students in:

- Introductory **Biostatistics**
- **Ecology** and environmental science
- **Biological research methods** or experimental design courses

Best used after students have been introduced to the concept of hypothesis testing and are learning to choose between a t-test and ANOVA. Can be used independently or guided by an instructor during lecture.

---

## What the Tool Does

### Controls

| Control | What it does |
|---|---|
| **2 / 3 / 4 groups** | Switches between an independent t-test (2 groups) and one-way ANOVA (3–4 groups). The summary table, distribution plot, and appropriate-test label all update automatically. |
| **Group separation slider** | Moves group means apart (increases the signal). Dragging right increases between-group variance and grows the F-ratio. |
| **New sample** | Redraws random data with the same settings — lets students see how results vary across samples from the same population. |

### Visualizations

**Dot plot** — shows all data points for each group with individual means (colored vertical bars) and within-group spread (blue bands). Orange arrows show the distance from each group mean to the grand mean — these are the "between-group" component of variance. The dashed vertical line marks the grand mean.

**SS breakdown bar** — a proportional stacked bar showing what fraction of total variance is SS_between (orange/explained) vs. SS_within (blue/unexplained). Watching this bar while moving the separation slider makes the ANOVA logic immediate.

**Summary table** — displays SS, df, MS, and the test statistic (F or t) with p-value. Switches automatically between a T-Test table and an ANOVA table depending on the number of groups selected.

**Distribution plot** — shows the F-distribution (or t-distribution for 2 groups) with the observed test statistic marked and the p-value shaded as a tail area. Seeing the shaded region shrink as the test statistic grows makes the p-value intuitive rather than abstract.

**T-test ↔ ANOVA link** — when 2 groups are selected, a callout shows that F = t² exactly, demonstrating that the t-test is a special case of ANOVA.

**T-Test vs. ANOVA comparison panel** — a side-by-side reference card covering when to use each test, the test statistic formula, degrees of freedom, and the role of post-hoc tests.

---

## Student Tasks

The tool includes **8 guided tasks** designed to be worked through in order, each with an optional hint. Tasks are designed to develop conceptual understanding, not just computational skill:

1. What happens to the test statistic when group means are identical?
2. How does increasing separation change the p-value — and what does that look like visually?
3. Verify that F = t² when k = 2 groups.
4. Confirm that SS_between + SS_within = SS_total by hand.
5. Click "New sample" repeatedly — does the p-value change? What does sampling variability mean for interpreting results?
6. Interpret the F-distribution chart: what does the shaded area actually represent?
7. Find a non-significant result and describe what the dot plot looks like when noise swamps signal.
8. Calculate the inflated Type I error rate from running multiple t-tests instead of ANOVA, and explain why ANOVA protects against this.

Students can click the numbered circle next to each task to mark it complete, and toggle hints on and off independently.

---

## Key Concepts Covered

- **Partitioning variance:** SS_total = SS_between + SS_within
- **The F-ratio:** mean square between ÷ mean square within (signal ÷ noise)
- **Degrees of freedom** for between-group (k − 1) and within-group (N − k) sources
- **The F and t distributions** and how the p-value is read as a tail area
- **The t-test as a special case of ANOVA** (F = t² when df₁ = 1)
- **Type I error inflation** from multiple comparisons and why ANOVA is the solution
- **Sampling variability** — why p-values shift across samples from the same population
- **When to use post-hoc tests** (Tukey, Bonferroni) after a significant ANOVA

---

## License

MIT — free to use, adapt, and share for educational purposes.
