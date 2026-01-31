# Blog Starter

A minimal Quarto blog configured for computational physics writing.

## Setup

### 1. Install Quarto

**macOS:**
```bash
brew install quarto
```

**Linux:**
Download from [quarto.org](https://quarto.org/docs/get-started/)

### 2. Install uv (Python package manager)

```bash
brew install uv
```

### 3. Install Python dependencies

In your blog directory, create a virtual environment and install dependencies:

```bash
uv venv
uv pip install jupyter pyyaml numpy matplotlib
```

### 4. Install fonts (optional but recommended)

The theme uses Source Serif 4, Source Sans 3, and JetBrains Mono. These are loaded from Google Fonts, so they'll work without installation, but installing them locally improves preview speed.

**macOS:**
```bash
brew install --cask font-source-serif-4 font-source-sans-3 font-jetbrains-mono
```

### 5. Copy these files to your blog directory

```
your-blog/
├── _quarto.yml
├── custom.scss
├── styles.css
├── computational_physics.mplstyle
├── index.qmd
├── about.qmd
└── posts/
    └── (your posts here)
```

### 6. Preview locally

```bash
uv run quarto preview
```

This opens a browser with live reload.

### 7. Publish to GitHub Pages

```bash
uv run quarto publish gh-pages
```

This builds the site and pushes to the `gh-pages` branch.

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

Then write in Markdown. Use `$...$` for inline math, `$$...$$` for display math.

## Including code

Python code that executes:

````markdown
```{python}
import numpy as np
print(np.pi)
```
````

Code that doesn't execute (just display):

````markdown
```python
# This is just shown, not run
x = 1
```
````

## Including figures

From Python:

````markdown
```{python}
#| label: fig-example
#| fig-cap: "Caption goes here."

import matplotlib.pyplot as plt
plt.style.use('computational_physics.mplstyle')

# Your plot...
plt.show()
```
````

## Interactive visualizations

Use Observable JS:

````markdown
```{ojs}
viewof x = Inputs.range([0, 10], {value: 5, label: "x"})

Plot.plot({
  marks: [
    Plot.line(data, {x: "time", y: "value"})
  ]
})
```
````

## Sidenotes

Use the margin column:

```markdown
Some text in the main column.

::: {.column-margin}
This appears in the margin as a sidenote.
:::
```

## Customization

- Edit `_quarto.yml` for site-wide settings
- Edit `custom.scss` for colors and typography
- Edit `styles.css` for layout adjustments
- Edit `computational_physics.mplstyle` for matplotlib defaults

## File structure after setup

```
your-blog/
├── _quarto.yml           # Site configuration
├── custom.scss           # Theme (colors, fonts)
├── styles.css            # Additional styles
├── computational_physics.mplstyle  # Matplotlib style
├── index.qmd             # Home page
├── about.qmd             # About page
├── posts/                # Your posts
│   ├── 01-first-post/
│   │   └── index.qmd
│   └── 02-second-post/
│       └── index.qmd
├── .venv/                # Python environment (add to .gitignore)
└── docs/                 # Generated site (don't edit)
```
