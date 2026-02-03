# Eigenbeam

A computational physics blog built with Quarto, hosted on Cloudflare Pages.

**Live site:** [eigenbeam.org](https://eigenbeam.org)

## Local development

### Prerequisites

- [Quarto](https://quarto.org): `brew install quarto`
- [uv](https://github.com/astral-sh/uv): `brew install uv`

### Setup

```bash
uv venv
uv pip install jupyter pyyaml numpy matplotlib
```

### Preview

```bash
uv run quarto preview
```

Opens a browser with live reload at `localhost:4200`.

## Deployment

Push to `main` and Cloudflare Pages builds automatically. The build command is:

```
curl -LO https://quarto.org/download/latest/quarto-linux-amd64.deb && dpkg -x quarto-linux-amd64.deb /tmp/quarto && export PATH=/tmp/quarto/opt/quarto/bin:$PATH && pip install uv && uv venv && uv pip install jupyter pyyaml numpy matplotlib && uv run quarto render
```

Output directory: `docs`

## Writing posts

Create a new directory under `posts/` for each post:

```
posts/
└── my-new-post/
    └── index.qmd
```

Each post starts with YAML front matter:

```yaml
---
title: "Post title"
date: 2025-02-15
description: "One sentence summary."
---
```

Use `$...$` for inline math, `$$...$$` for display math.

## Including figures

```python
#| label: fig-example
#| fig-cap: "Caption goes here."

import matplotlib.pyplot as plt
plt.style.use('computational_physics.mplstyle')

# Your plot...
plt.show()
```

## Sidenotes

```markdown
Some text in the main column.

::: {.column-margin}
This appears in the margin as a sidenote.
:::
```

## Customization

- `_quarto.yml` — site-wide settings
- `custom.scss` — colors and typography
- `styles.css` — layout adjustments
- `computational_physics.mplstyle` — matplotlib defaults
