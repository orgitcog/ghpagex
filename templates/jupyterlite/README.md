# JupyterLite - Jupyter in the Browser

Deploy interactive Jupyter notebooks that run entirely in the browser using Pyodide and WebAssembly.

## Overview

JupyterLite is a distribution of JupyterLab that runs entirely in the browser, with no Python server required. It uses Pyodide (Python compiled to WebAssembly) to execute code directly in the browser.

## Features

- **Full Python Stack**: NumPy, Pandas, Matplotlib, SciPy, and more
- **No Backend Required**: Everything runs client-side
- **Persistent Storage**: Notebooks saved in browser storage
- **Interactive Widgets**: ipywidgets support
- **Fast Loading**: Progressive web app with service workers

## Use Cases

- **Education**: Interactive Python courses and tutorials
- **Documentation**: Live code examples in technical docs
- **Data Science Demos**: Showcase analyses without server costs
- **Scientific Computing**: Publish reproducible research
- **Portfolio Projects**: Interactive data visualizations

## Prerequisites

- Python 3.8+ (for building)
- Jupyter notebooks or `.ipynb` files
- `jupyter-lite` Python package

## Quick Start

### 1. Install JupyterLite

```bash
pip install jupyterlite-core jupyterlite-pyodide-kernel
```

### 2. Prepare Content

```bash
mkdir content
# Add your .ipynb files to content/
```

### 3. Build the Site

```bash
jupyter lite build --contents content --output-dir _site
```

### 4. Deploy

Use the provided GitHub Actions workflow to deploy to Pages.

## Deployment Workflow

```yaml
name: Deploy JupyterLite

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'
      
      - name: Install JupyterLite
        run: |
          pip install jupyterlite-core jupyterlite-pyodide-kernel
      
      - name: Build JupyterLite
        run: |
          jupyter lite build --contents content --output-dir _site
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '_site'
  
  deploy:
    needs: build
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

## Project Structure

```
your-repo/
├── content/                    # Your Jupyter notebooks
│   ├── intro.ipynb
│   ├── data_analysis.ipynb
│   └── visualization.ipynb
├── requirements.txt            # Python dependencies for Pyodide
├── jupyter_lite_config.json   # Configuration (optional)
└── .github/
    └── workflows/
        └── deploy.yml
```

## Configuration

### jupyter_lite_config.json

```json
{
  "LiteBuildConfig": {
    "contents": ["content"],
    "output_dir": "_site"
  },
  "PipliteAddon": {
    "piplite_urls": [
      "https://pypi.org/simple"
    ]
  }
}
```

### requirements.txt

Specify additional packages to pre-install:

```
numpy
pandas
matplotlib
scipy
scikit-learn
plotly
```

## Advanced Features

### Custom Extensions

Install JupyterLab extensions:

```bash
pip install jupyterlab-some-extension
jupyter lite build
```

### Pre-populated Data

Include datasets in your repository:

```
content/
├── data/
│   ├── dataset.csv
│   └── large_file.parquet
└── notebooks/
    └── analysis.ipynb
```

### Custom Kernels

Add support for other languages:

```bash
pip install jupyterlite-xeus-python  # Faster Python kernel
pip install jupyterlite-javascript-kernel
```

## Available Packages

JupyterLite includes many popular scientific packages out-of-the-box:

- **Core**: NumPy, Pandas, Matplotlib
- **Visualization**: Plotly, Altair, Bokeh
- **Machine Learning**: scikit-learn
- **Statistics**: SciPy, statsmodels
- **Data**: SQLite, lxml, beautifulsoup4

## Performance Considerations

- **First Load**: Initial download ~30-50MB (cached afterward)
- **Execution Speed**: ~2-5x slower than native Python
- **Memory**: Limited by browser (typically 1-4GB)
- **File Size**: Keep notebooks under 10MB for best UX

## Examples

### Data Visualization Notebook

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load data
df = pd.read_csv('data/sales.csv')

# Create visualization
df.plot(x='date', y='revenue', kind='line')
plt.title('Revenue Over Time')
plt.show()
```

### Machine Learning Demo

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier

# Load data
iris = load_iris()
X_train, X_test, y_train, y_test = train_test_split(
    iris.data, iris.target, test_size=0.3
)

# Train model
clf = RandomForestClassifier()
clf.fit(X_train, y_train)

# Evaluate
score = clf.score(X_test, y_test)
print(f"Accuracy: {score:.2f}")
```

## Alternatives

- **Pyodide REPL**: Minimal Python interpreter in browser
- **Basthon**: French educational Python environment
- **Brython**: Python syntax running as JavaScript
- **Skulpt**: Python-to-JavaScript transpiler

## Resources

- [JupyterLite Documentation](https://jupyterlite.readthedocs.io/)
- [Pyodide Documentation](https://pyodide.org/)
- [JupyterLite Demo](https://jupyterlite.github.io/demo/)
- [Example Deployments](https://github.com/jupyterlite/demo)

## Limitations

- Not all Python packages available (must be pure Python or have WASM builds)
- No filesystem access beyond browser storage
- Performance depends on browser and device
- Limited multiprocessing/threading support
- Cannot make arbitrary network requests (CORS restrictions)

## Tips

1. **Optimize Notebooks**: Keep cells small and focused
2. **Use Caching**: Leverage browser cache with service workers
3. **Lazy Loading**: Load large datasets on demand
4. **Mobile Friendly**: Test on various screen sizes
5. **Documentation**: Include README notebooks explaining your project
6. **Version Control**: Use `.gitignore` to exclude `_site/` build directory

## Best Practices

- Keep total repository size under 1GB
- Use compressed data formats (Parquet instead of CSV)
- Include a landing page notebook
- Add interactive widgets for engagement
- Provide clear instructions in markdown cells
- Test in multiple browsers (Chrome, Firefox, Safari)
