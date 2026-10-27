# ANOVA Explorer

An interactive, browser-based tool for biostatistics students to build a deep visual understanding of one-way ANOVA and the independent t-test — how they partition variance, when to use each, and what the F and t distributions actually mean — plus a worked class example where students fill in the ANOVA table themselves.

🔗 **[Launch ANOVA Explorer](https://lizferguson5.github.io/anova-explorer/)**

---

## Overview

Students often learn ANOVA as a formula to apply rather than a concept to understand. This tool makes the logic concrete: you can see the between-group signal and within-group noise drawn directly on the data, watch the F-ratio and p-value respond in real time as you move a slider, and compare the t-test and ANOVA side by side to understand when — and why — they are mathematically identical.

The app has two tabs:

1. **Explorer: ANOVA vs t-test** — simulated antibiotic-trial data with sliders and guided tasks.
2. **Class example: Antibiotic trial** — an in-app worksheet where students calculate the summary statistics and the full ANOVA table by hand, with instant checking and step-by-step help.

Everything is computed live in the browser. No software installation required.

---

## Data Description

Both tabs use the same scenario: **patients with a bacterial skin infection were randomly assigned to one of three antibiotics, and researchers recorded the number of days until each patient's infection cleared** (fewer days = better).

- **Factor:** antibiotic (A, B, C) · **Response:** days until infection cleared
- **H₀:** μ<sub>A</sub> = μ<sub>B</sub> = μ<sub>C</sub> · **Hₐ:** at least one mean is different

### Class example data (Tab 2)

The numbers are invented for teaching. They were chosen so the hand calculations come out to whole numbers, and the group sizes are unequal (a few patients "dropped out") so the grand mean has to be weighted by n.

| Antibiotic | Days until infection cleared | n | Mean | Variance (s²) |
|---|---|---|---|---|
| A | 12, 16, 10, 17, 11, 12 | 6 | 13 | 8 |
| B | 9, 13, 7, 11, 16, 9, 12 | 7 | 11 | 9 |
| C | 4, 10, 2, 6, 3 | 5 | 5 | 10 |

**Answer key:** grand mean = 10 (the unweighted average of the means, 9.67, is a deliberate trap) · SS(B) = 186 · SS(W) = 134 · SS(T) = 320 · df = 2, 15, 17 · MS(B) = 93 · MS(W) = 8.93 · **F(2, 15) = 10.41, p = .0015**

**Tukey post-hoc:** C differs from A (p = .001) and from B (p = .010), but A vs B is not significant (p = .47). This supports a discussion of whether "not significant" means "works equally well."

Students (or instructors) can replace these numbers with their own data — any three groups with at least two values each — and the whole worksheet recalculates.

### Explorer data (Tab 1)

Randomly simulated each time: 12 patients per antibiotic, average recovery time starting at 24 days, patient-to-patient SD ≈ 3 days. The slider sets the true difference (0–6 days) between neighbouring antibiotics.

---

## What the Tool Does

### Tab 1 — Explorer

| Control | What it does |
|---|---|
| **2 / 3 / 4 groups** | Switches between an independent t-test (2 groups) and one-way ANOVA (3–4 groups). The table, distribution plot, and appropriate-test label update automatically. |
| **True difference slider** | Sets how far apart the antibiotics' true mean recovery times are (the signal). Dragging right increases between-group variance and grows the F-ratio. |
| **New sample** | Redraws random patients with the same settings — shows how results vary across samples from the same population. |

**Dot plot** — every patient's recovery time by antibiotic, with group means (colored bars), ±1 SD spread (blue bands), the grand mean (dashed line), and orange arrows showing each group mean's distance from the grand mean (the between-group component).

**SS breakdown bar** — proportion of total variation that is SS_between (signal) vs. SS_within (noise).

**ANOVA summary table** — SS, df, MS, F and p-value. With 2 groups, a callout shows the matching t-test and that t² = F.

**F-distribution plot** — the observed F marked, with the p-value shaded as the right-tail area.

**T-Test vs. ANOVA comparison panel** — when to use each test, the test statistic, degrees of freedom, and post-hoc options.

### Tab 2 — Class example (in-app worksheet)

Students type answers directly into two tables, mirroring the paper data sheet:

1. **Summary statistics** — mean, variance and standard deviation for each antibiotic. An **All patients** column at the right holds N (in the sample-size row) and the grand mean (at the end of the Mean row), followed by k.
   - **Variance helper:** below the table, a worksheet for each antibiotic lists every x and fills in x − x̄ once that group's mean is right. Students square a couple of deviations themselves, then click **Fill the rest**. The sum Σ(x − x̄)² appears automatically, ready to divide by n − 1. A non-squared or negative entry gets a reminder to square it. The same sums add up to SS(W) later.
2. **ANOVA table** — SS, df, MS and F for Between, Within and Total. The p-value appears once F is correct.

Each box turns **green** when correct (rounding within ~1.5% is accepted) or **red** when not. A help panel follows whichever box the student is in, with the formula, a **💡 Hint** (their numbers plugged in), and **Show work** (the full calculation). Common mistakes get targeted feedback — dividing the variance by n, averaging the means without weighting, using N − 1 for df(W), putting F upside down, and more.

After the tables, three more parts unlock in order:

3. **p-value and decision** — F-distribution with the critical value at α = .05; students choose reject / fail to reject.
4. **Tukey post-hoc** — students tick which pairs they think differ, then check against Tukey-Kramer results.
5. **Write it up** — a sentence starter, a discussion prompt, **Copy results** (full table + Tukey output to paste into Nearpod or Canvas), and a **CSV download** to rerun the analysis in jamovi.

**Instructor view** fills in every answer for projecting.

---

## Student Tasks (Tab 1)

The Explorer includes **9 guided tasks**, each with an optional hint. Tasks marked *Check-in* are designed for answers to be collected in class (Nearpod / Canvas).

1. What happens to the test statistic when the antibiotics truly don't differ? How often is p < .05 anyway?
2. How large a true difference is needed before results are significant most of the time?
3. *Check-in:* Square t and compare it to F with 2 groups — what does this say about the t-test and ANOVA?
4. Confirm that SS_between + SS_within = SS_total.
5. *Check-in:* Click "New sample" five times — does the conclusion change? What does that mean for a single trial?
6. Interpret the shaded area on the F-distribution.
7. Find a non-significant result and describe what the dot plot looks like when noise swamps signal.
8. *Check-in:* Calculate the inflated Type I error rate from running multiple t-tests instead of ANOVA.
9. *After Tab 2:* Use a true difference of 2 days to explore power — does "not significant" mean "no difference"?

---

## Companion Document

**`One_Way_Anova_Doc.docx`** is a printable backup of the class example (useful if devices or wifi aren't available). It provides:

- the antibiotic-trial scenario and data
- blank summary-statistics and ANOVA tables to fill in by hand, with an All patients column for N and the grand mean (matching the app)
- the grand-mean formula
- four shaded **Nearpod check-in** questions placed at the matching points in the lecture (hypotheses, grand mean, decision, post-hoc)
- a pointer back to Tab 2 for hints and worked solutions

---

## Key Concepts Covered

- **Partitioning variance:** SS_total = SS_between + SS_within
- **Summary statistics by hand:** mean, variance (dividing by n − 1), standard deviation, weighted grand mean
- **The F-ratio:** mean square between ÷ mean square within (signal ÷ noise)
- **Degrees of freedom** for between-group (k − 1) and within-group (N − k) sources
- **The F and t distributions** and how the p-value is read as a tail area
- **The t-test as a special case of ANOVA** (F = t² when df₁ = 1)
- **Type I error inflation** from multiple comparisons and why ANOVA is the solution
- **Sampling variability and power** — why p-values shift across samples, and why "not significant" ≠ "no effect"
- **Tukey post-hoc tests** after a significant ANOVA, and the equal-variance assumption check

---

## Files

| File | What it is |
|---|---|
| `index.html` | The app (served at the Live Demo link) |
| `One_Way_Anova_Doc.docx` | Printable class-example handout with check-in questions |
| `LICENSE` | MIT license |

---

## License

MIT — free to use, adapt, and share for educational purposes.
