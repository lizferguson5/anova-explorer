# ANOVA Explorer

An interactive, browser-based tool that helps biostatistics students see where the variation in a one-way ANOVA comes from (**total**, **between-group** and **within-group / residual error**), plus a worked class example where students fill in the ANOVA table themselves.

🔗 **[Launch ANOVA Explorer](https://lizferguson5.github.io/anova-explorer/)**

---

## Overview

Students often learn ANOVA as a formula to apply rather than a concept to understand, and many mix up between-group, within-group, residual and error variation. This tool makes the sources of variation visible: every patient's deviation is drawn as a line, color-coded by source, and animated so students can watch the total variation split into a between-group piece and a within-group (residual) piece.

The app has two tabs:

1. **Sources of variation** — an animated, step-by-step walkthrough of total, between-group and within-group (residual / error) variation, followed by a "Try it yourself" playground.
2. **Class example: Antibiotic trial** — an in-app worksheet where students calculate the summary statistics and the full ANOVA table by hand, with instant checking and step-by-step help.

Both tabs use the same 18 patients, so the variation students see in Tab 1 is exactly what they calculate in Tab 2. Everything is computed live in the browser. No software installation required.

---

## Data Description

Both tabs use the same scenario: **patients with a bacterial skin infection were randomly assigned to one of three antibiotics, and researchers recorded the number of days until each patient's infection cleared** (fewer days = better).

- **Factor:** antibiotic (A, B, C) · **Response:** days until infection cleared
- **H₀:** μ<sub>A</sub> = μ<sub>B</sub> = μ<sub>C</sub> · **Hₐ:** at least one mean is different

### Class example data (both tabs)

The numbers are invented for teaching. They were chosen so the hand calculations come out to whole numbers, and the group sizes are unequal (a few patients "dropped out") so the grand mean has to be weighted by n.

| Antibiotic | Days until infection cleared | n | Mean | Variance (s²) |
|---|---|---|---|---|
| A | 12, 16, 10, 17, 11, 12 | 6 | 13 | 8 |
| B | 9, 13, 7, 11, 16, 9, 12 | 7 | 11 | 9 |
| C | 4, 10, 2, 6, 3 | 5 | 5 | 10 |

**Answer key:** grand mean = 10 (the unweighted average of the means, 9.67, is a deliberate trap) · SS(B) = 186 · SS(W) = 134 · SS(T) = 320 · df = 2, 15, 17 · MS(B) = 93 · MS(W) = 8.93 · **F(2, 15) = 10.41, p = 0.0015**

**Tukey post-hoc:** C differs from A (p = 0.001) and from B (p = 0.010), but A vs B is not significantly different (p = 0.470). This supports a discussion of whether "not significant" means "works equally well."

Students (or instructors) can replace these numbers with their own data — any three groups with at least two values each — and the whole worksheet recalculates.

### Playground data (Tab 1)

The "Try it yourself" sliders rescale the class data rather than generating new random data. One slider stretches or shrinks each group mean's distance from the grand mean (the between-group signal); the other stretches or shrinks each patient's distance from their own group mean (the within-group noise). At the default settings the playground shows the class data exactly. If stretching would push recovery times below zero, all values are shifted up together, which changes the grand mean but none of the sums of squares.

---

## What the Tool Does

### Tab 1 — Sources of variation

Three color-coded cards define the sources, with the alternative names students will meet:

| Source | Color | What it measures | Also called |
|---|---|---|---|
| **Total** | gray | each patient's distance from the grand mean | |
| **Between groups** | orange | each group mean's distance from the grand mean (explained by which antibiotic) | treatment, among-groups, signal |
| **Within groups** | blue | each patient's distance from their own group mean (not explained by the antibiotic) | **residual**, **error**, noise |

Group colors (purple, green, magenta) are deliberately different from the gray / orange / blue line colors so the two are never confused. Every plot labels the axes with the course terms: **Response variable** (days until infection cleared) on the y-axis and **Factor variable** (antibiotic) along the bottom.

**Animated walkthrough (8 steps).** Each step plays a short animation with a prompt telling students what to watch, and a running readout of the sums of squares. Use **Back / Next / Replay**, the step dots, or the **← →** arrow keys when projecting.

1. **Every patient is different:** all 18 patients mixed together, with the grand mean (10 days) drawn across.
2. **Total variation:** gray lines grow from the grand mean to each patient; SS(T) counts up to 320.
3. **Sort the patients by antibiotic:** dots animate into their three groups and the group means appear.
4. **Between groups (the signal):** the patients stay in place (faded) and **one orange line per group** is drawn from that group's mean to the grand mean, labeled ×n to show it is counted once per patient; SS(B) = 6(3)² + 7(1)² + 5(−5)² = 186.
5. **Within groups (residual error):** dots slide back to their real values; blue lines show each patient's distance from their own group mean; SS(W) = 40 + 54 + 40 = 134.
6. **One patient, split in two:** a single patient (17 days on Antibiotic A) is highlighted and their total deviation (+7) is drawn next to its two pieces, between (+3) and within (+4).
7. **Add it all up:** SS(T) 320 = SS(B) 186 + SS(W) 134 as a stacked bar.
8. **From sums of squares to F:** each SS bar splits into its degrees of freedom (2 pieces for between, 15 for within) to give the mean squares, MS(B) = 186 ÷ 2 = 93 and MS(W) = 134 ÷ 15 = 8.93. One piece of each is then compared side by side: F = between-group MS ÷ within-group MS = 10.41.

**Try it yourself.** Two sliders (*how different the antibiotics are* and *how much patients vary on the same antibiotic*) and toggles for the total, between and within lines. A stacked bar shows what share of the total variation is between vs. within, with a live ANOVA table (SS, df, MS, F, p) and a plain-language verdict. As in the walkthrough, between-group variation is one orange line per group. Three short "Try" prompts guide what to drag and what to watch.

### Tab 2 — Class example (in-app worksheet)

Students type answers directly into two tables, mirroring the paper data sheet:

1. **Summary statistics** (with a **Fill in all summary statistics** button) — mean, variance and standard deviation for each antibiotic. An **All patients** column at the right holds N (in the sample-size row) and the grand mean (at the end of the Mean row), followed by k.
   - **Variance helper:** below the table, a worksheet for each antibiotic lists every x and fills in x − x̄ once that group's mean is right. Students square a couple of deviations themselves, then click **Fill the rest**. The sum Σ(x − x̄)² appears automatically, ready to divide by n − 1. A non-squared or negative entry gets a reminder to square it. The same sums add up to SS(W) later.
2. **ANOVA table** (with a **Fill in the ANOVA table** button) — SS, df, MS and F for Between, Within and Total. The p-value appears once F is correct, shown with a leading zero (0.0015).

Each box turns **green** when correct (rounding within ~1.5% is accepted) or **red** when not. A help panel follows whichever box the student is in, with the formula, a **💡 Hint** (their numbers plugged in), and **Show work** (the full calculation). Common mistakes get targeted feedback — dividing the variance by n, averaging the means without weighting, using N − 1 for df(W), putting F upside down, and more.

After the tables, three more parts unlock:

3. **p-value and decision** — a short explanation of the F-distribution (a ratio of two variances, close to 1 when H₀ is true, never negative, right-skewed, shaped by df₁ = k − 1 and df₂ = N − k), the F curve with the critical value and p-value area, and an **F-table of critical values for α = 0.05** with the student's df₁ column and df₂ row highlighted so they can see where the critical value (3.68) comes from. Students then choose reject / fail to reject.
4. **Tukey post-hoc test** — the Tukey-Kramer results table (mean difference, Tukey p-value, and "Significantly different" / "Not significantly different" spelled out), a plain-language summary, and **"How Tukey works, in 4 steps"**: (1) find the gap between each pair of means; (2) divide it by its standard error, √(MS(W) ÷ n), using the harmonic mean of the two sample sizes, to get **q**; (3) compare q with the critical value from the studentized range distribution (3.67 for k = 3, df = 15); (4) software turns q into an adjusted p-value. A worked table shows the gap, harmonic-mean n, standard error and q for every pair.
5. **Write it up for a research paper** — a model Results paragraph (test, F(df₁, df₂), p, direction of the differences, post-hoc results), **Table 1** (n and mean ± SD for each antibiotic, with Tukey grouping letters) and **Table 2** (the ANOVA table), plus a "what goes where" guide to text vs. tables vs. figures. A **CSV download** lets students rerun the analysis in jamovi.

**Calculator.** A 🧮 **Calculator** button (bottom-right, on both tabs) opens a calculator with brackets, square, square root and powers, so students can work out squared deviations and divisions without leaving the page. Past answers can be clicked to reuse them.

**Instructor view** fills in every answer for projecting.

---

---

## Companion Document

**`One_Way_Anova_Doc.docx`** is a printable backup of the class example (useful if devices or wifi aren't available). It provides:

- the antibiotic-trial scenario and data
- blank summary-statistics and ANOVA tables to fill in by hand, with an All patients column for N and the grand mean (matching the app)
- the grand-mean formula
- six shaded **Nearpod check-in** questions placed at the matching points in the lecture: hypotheses, sources of variation (two questions on between vs. within / residual error), grand mean, decision, and post-hoc
- a pointer back to Tab 2 for hints and worked solutions

---

## Key Concepts Covered

- **Sources of variation:** total, between-group (treatment / signal) and within-group (residual / error / noise), and that "within", "residual" and "error" name the same thing
- **Partitioning variation:** each patient's deviation splits as (x − x̿) = (x̄ − x̿) + (x − x̄), so SS(T) = SS(B) + SS(W)
- **Summary statistics by hand:** mean, variance (dividing by n − 1), standard deviation, weighted grand mean
- **The F-ratio:** MS(B) ÷ MS(W), between-group signal compared with residual error
- **Degrees of freedom** for between-group (k − 1) and within-group (N − k) sources
- **The F distribution** and how the p-value is read as a tail area
- **Tukey post-hoc tests** after a significant ANOVA, and the equal-variance assumption check

---

## Files

| File | What it is |
|---|---|
| `index.html` | The app (served at the Launch ANOVA Explorer link) |
| `One_Way_Anova_Doc.docx` | Printable class-example handout with check-in questions |
| `LICENSE` | MIT license |

---

## License

MIT — free to use, adapt, and share for educational purposes.
