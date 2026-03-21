# SKILL.md — Engineering Tools Project

## What this project is

A Hugo static site published at https://endofwave.github.io/engineering-tools/
with two series of content for mechanical engineers:

- **Series A — Papers → Tools:** calculation pipelines extracted from
  technical papers, with Python notebooks runnable on Google Colab.
- **Series B — Open Formula:** complete derivations of recurring
  structural formulas, from first principles to final boxed result.

Author: G. Ganz, mechanical engineer.
GitHub repo: https://github.com/endofwave/engineering-tools

---

## Project structure

```
C:\Progetti\engineering-tools\
├── .github/workflows/hugo.yaml    ← GitHub Actions deploy
├── content/
│   ├── _index.md                  ← Home page
│   ├── about/
│   │   ├── index.md               ← About page
│   │   └── cover.png
│   ├── search.md
│   ├── series-a/
│   │   ├── _index.md              ← Series A list page
│   │   ├── cover.png
│   │   ├── a1-fatigue-notched-plate/
│   │   │   ├── index.md
│   │   │   └── prepomax-stress-result.png
│   │   └── a2-hertz-contact/
│   │       ├── index.md
│   │       ├── hertz_contact_6206.png
│   │       ├── hertz_parametric_6206.png
│   │       └── hertz_pipeline_infographic.png
│   └── series-b/
│       ├── _index.md              ← Series B list page
│       ├── cover.png
│       ├── b1-euler-bernoulli/
│       │   ├── index.md
│       │   ├── beam-bending-strain.png
│       │   ├── moment-integration.png
│       │   └── curvature-geometry.png
│       ├── b2-euler-buckling/
│       │   ├── index.md
│       │   ├── column-pinned-setup.png
│       │   └── buckling-mode-shape.png
│       ├── b3-curvature/
│       │   ├── index.md
│       │   ├── curvature-geometry.png
│       │   └── exact-vs-linearised.png
│       └── b4-cantilever/
│           ├── index.md
│           ├── cantilever-setup.png
│           └── deflection-curve.png
├── hugo.yaml                      ← Site configuration
├── layouts/                       ← KaTeX partials and render hooks
├── static/
│   ├── img/
│   └── notebooks/                 ← Colab notebooks (.ipynb)
├── themes/PaperMod/               ← Theme (git submodule)
└── SKILL.md                       ← This file
```

---

## Hugo conventions

- **Theme:** PaperMod via git submodule
- **Math:** KaTeX via layouts/partials/extend_head.html.
  Delimiters: `$...$` inline, `$$...$$` block.
  Configured in hugo.yaml under markup.goldmark.extensions.passthrough.
- **Images:** page bundles. Each post is a folder with index.md and
  its images. Reference images with relative paths: `![alt](filename.png)`
- **Front matter** for posts:

```yaml
---
title: "Title here"
date: 2026-03-20
math: true
tags:
  - tag1
  - tag2
summary: "One-line summary for the list page."
---
```

- **Front matter** for list pages (_index.md):

```yaml
---
title: "Series title"
description: "One-line description"
---
```

- **Colab notebooks** go in `static/notebooks/`. Link format:
  `https://colab.research.google.com/github/endofwave/engineering-tools/blob/main/static/notebooks/FILENAME.ipynb`
- **Deploy:** automatic via GitHub Actions on push to main.
  Workflow file: .github/workflows/hugo.yaml, Hugo version 0.158.0.
- **Publish workflow:** modify files → commit → push (via GitHub Desktop
  or Git Bash: `git add -A` → `git commit -m "message"` → `git push`)

---

## Series A — How to create a new tool

Each tool follows this structure:

1. **Quick Example** — teaser: input → boxed result → engineering
   verdict → summary table. Readable in 30 seconds.
2. **Pipeline Overview** — block diagram (infographic or ASCII chain)
3. **Nodes 1–N** — for each node: purpose, input table, formula,
   output table
4. **Numerical case** — node-by-node calculation with intermediate values
5. **Plots** — figures from the notebook
6. **How to use the notebook** — requirements, parameters, limitations
7. **References**

### Technical specs
- Notebook: only numpy and matplotlib. No other dependencies.
- Notebook link: Google Colab format (see above)
- Language: English
- Tone: technical, direct. The reader is an engineer applying the method.
- When the source paper has errors: identify, correct, document.

### To add a new tool (e.g., A3):
1. Create `content/series-a/a3-short-name/`
2. Create `index.md` with front matter + content following the structure above
3. Put all images in the same folder
4. Put the notebook in `static/notebooks/`
5. Commit and push

---

## Series B — How to create a new derivation

Each derivation follows these rules:

### Structure
- **Opening:** 1–2 sentences on what we want to obtain
- **Pipeline:** numbered formulas (1), (2), (3)... with explicit
  cross-references ("(3) into (7)"), validity limits stated next
  to each formula
- **Figures:** integrated in the flow, not decorative
- **Closing:** final formula in a box (`$$\boxed{...}$$`) +
  assumption list in the order they entered, with formula number

### Style rules
- Tone: dry, technical. No didactic tone.
  The reader is an engineer who verifies, not a student.
- Language: English
- Formulas: numbered with `\tag{N}`, cross-referenced explicitly
- Validity limits: stated immediately after the formula they apply to
- Assumptions table at the end: Assumption | Where it entered | Formula

### To add a new derivation (e.g., B5):
1. Create `content/series-b/b5-short-name/`
2. Create `index.md` with front matter + content following the rules above
3. Put all figures in the same folder (use descriptive names, not
   "Pasted image...")
4. Commit and push

---

## Converting from Obsidian to Hugo

When converting Obsidian markdown to Hugo:

1. **Images:** replace `![[Pasted image 20260318125830.png]]`
   with `![Descriptive alt text](descriptive-name.png)`
   and rename the file accordingly.
2. **Image size syntax:** remove Obsidian size hints like `|419`
   (e.g., `![[image.png|419]]` → `![alt](image.png)`)
3. **Front matter:** add Hugo front matter (title, date, math: true,
   tags, summary)
4. **Math:** LaTeX delimiters `$` and `$$` work as-is (same in both)
5. **Internal links:** replace `[[other note]]` with standard
   markdown links if needed
6. **Callouts/admonitions:** Obsidian `> [!note]` syntax does not
   render in Hugo. Convert to standard blockquotes or remove.

---

## Workflow 1 — Finding papers (use with Claude in Chrome)

When asked to find papers on a topic:

1. Search Google Scholar, ResearchGate, MDPI, ScienceDirect
   for open-access papers
2. Focus on papers that contain:
   - A clear analytical method or formula pipeline
   - Numerical verification cases
   - FEM comparison (preferred but not required)
3. For each paper found, record:
   - Title, authors, year, journal
   - Key method/formula
   - Whether it has a numerical example
   - Whether it's open access
   - URL
4. Save the summary as a markdown table in the project folder

### Good candidates for Series A:
- Papers with step-by-step calculation methods
- Papers that combine analytical + FEM approaches
- Papers with errors that can be identified and corrected
- Topics: contact mechanics, fatigue, fracture, vibrations,
  buckling, pressure vessels, bolted joints, bearings, gears

### Good candidates for Series B:
- Formulas used daily but rarely derived from scratch
- Formulas whose assumptions are often forgotten
- Formulas that appear in multiple textbooks with different
  notations but the same physics
- Topics: beam theory, plate theory, buckling, elasticity,
  energy methods, stress concentration factors

---

## Workflow 2 — Site maintenance tasks

Common tasks to run periodically:

- **Compress images:** find all PNG/JPG over 500 KB in content/
  and compress them to reduce page load time
- **Check links:** verify all internal links and external URLs
  in markdown files
- **Verify front matter:** ensure every index.md has title, date,
  math, tags, and summary
- **Check LaTeX:** look for common LaTeX issues (unescaped
  underscores, missing dollar signs)
- **Build test:** run `hugo` (no server) and check for warnings
  or errors in the output

---

## What NOT to do

- Do NOT modify files in `themes/PaperMod/` — it's a git submodule
- Do NOT commit the `public/` folder — it's in .gitignore
- Do NOT use `\begin{equation}` — use `$$...\tag{N}$$` instead
- Do NOT use Obsidian-style image syntax in Hugo files
- Do NOT add Python dependencies beyond numpy and matplotlib
  in notebooks
- Do NOT change hugo.yaml markup settings without testing locally first
