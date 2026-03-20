# Hertz Contact Stress Tool

Analytical pipeline for Hertzian contact stress in deep groove ball bearings.

**Live site:** `https://endofwave.github.io/hertz-contact-tool/`

## What's inside

| File | Description |
|:-----|:------------|
| `content/tools/hertz-contact/index.md` | Full pipeline documentation (5 nodes) with verification case |
| `static/notebooks/hertz_contact_stress_pipeline.ipynb` | Colab-ready notebook (theory + code fused) |
| `static/img/hertz_*.png` | Figures (pressure map, parametric plot) |

## Quick start

```bash
# 1. Clone
git clone https://github.com/endofwave/hertz-contact-tool.git
cd hertz-contact-tool

# 2. Add PaperMod theme
git submodule add --depth=1 \
  https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod

# 3. Local preview
hugo server -D
# → open http://localhost:1313/hertz-contact-tool/

# 4. Build for production
hugo --gc --minify
```

## Deploy to GitHub Pages

1. Push to GitHub (the repo name should match the `baseURL` path in `hugo.yaml`).
2. Go to **Settings → Pages → Source** and select **GitHub Actions**.
3. The workflow in `.github/workflows/hugo.yaml` builds and deploys automatically on push to `main`.

**Before pushing**, edit `hugo.yaml`:
- Update author name in `hugo.yaml` if desired.

## Customise

- **Add a new tool:** create `content/tools/new-tool/index.md` with the same front matter pattern.
- **Change theme colours:** override in `assets/css/extended/` (see PaperMod docs).
- **Add a blog section:** create `content/posts/` with `_index.md`.

## References

- Anoopnath et al. (2018), *Materials Today: Proceedings* 5, 3283–3288.
- Hamrock & Brewe (1983), *ASME J. Lub. Tech.* 105(2), 171–177.
- Harris & Kotzalas (2006), *Rolling Bearing Analysis*, 5th ed.

## License

Content: CC BY 4.0. Code: MIT.
