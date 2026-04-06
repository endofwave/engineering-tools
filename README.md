# Engineering Tools

Analytical calculation pipelines extracted from peer-reviewed papers and complete derivations of classical structural formulas — each with declared inputs, explicit intermediate steps, and a numerical verification case.

**Live site:** [endofwave.github.io/engineering-tools](https://endofwave.github.io/engineering-tools/)

No black boxes. Every formula is shown. Every number is traceable.

---

## Series A — Papers → Tools

Calculation pipelines restructured from peer-reviewed papers. Each tool ships with a Google Colab notebook (numpy + matplotlib, no other dependencies).

| Tool | Topic | Paper | Notebook |
|:-----|:------|:------|:---------|
| A1 | Fatigue life of notched plates | Hazizi et al. (2023) | [Open in Colab](https://colab.research.google.com/github/endofwave/engineering-tools/blob/main/static/notebooks/A1_fatigue_notched_plate.ipynb) |
| A2 | Hertz contact stress in deep groove ball bearings | Anoopnath et al. (2018) | [Open in Colab](https://colab.research.google.com/github/endofwave/engineering-tools/blob/main/static/notebooks/hertz_contact_stress_pipeline.ipynb) |
| A3 | Thick-walled cylinder stress analysis (n coaxial rings) | Croccolo & Vincenzi (2009) | [Open in Colab](https://colab.research.google.com/github/endofwave/engineering-tools/blob/main/static/notebooks/A3_thick_walled_cylinder.ipynb) |
| A4 | Penetration depth of rigid projectile into concrete | Li & Chen (2003) | [Open in Colab](https://colab.research.google.com/github/endofwave/engineering-tools/blob/main/static/notebooks/A4_penetration_depth.ipynb) |

## Series B — Open Formula

Complete derivations of recurring structural formulas, from first physical hypothesis to final boxed result.

| Formula | Title |
|:--------|:------|
| B1 | Derivation of EI·y″ = M(x) |
| B2 | Where P_cr = π²EI/L² comes from (Euler buckling) |
| B3 | Curvature of a plane curve: κ = y″/(1+y'²)^(3/2) |
| B4 | Where δ = PL³/(3EI) comes from (cantilever deflection) |

## How to use

**As a reader:** browse the [live site](https://endofwave.github.io/engineering-tools/). Each tool page walks through the calculation step by step.

**As a user:** click "Open in Colab" on any tool page, modify the input parameters cell, press Run All. No installation, no environment setup.

**As a developer:** clone the repo and run locally:

```bash
git clone https://github.com/endofwave/engineering-tools.git
cd engineering-tools
git submodule update --init --recursive
hugo server
```

Requires Hugo extended ≥ 0.158.0 and the PaperMod theme (included as submodule).

## Built with

- [Hugo](https://gohugo.io/) + [PaperMod](https://github.com/adityatelange/hugo-PaperMod/)
- GitHub Pages with GitHub Actions
- Python notebooks: numpy + matplotlib only

## Author

G. Ganz — Mechanical engineer

## License

Content: CC BY 4.0. Code: MIT.
