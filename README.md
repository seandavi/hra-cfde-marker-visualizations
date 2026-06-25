# hra-cfde-marker-visualizations

Visualizations for the CFDE Marker Paper 2026.

This repository contains reproducible Jupyter notebooks that generate
figures summarizing tissue-block (dataset) coverage across organs and
consortia in the [Common Fund Data Ecosystem (CFDE)](https://www.nih-cfde.org/),
using data from the [Human Reference Atlas (HRA)](https://humanatlas.io/).
The notebooks pull dataset counts per organ and per data-providing effort
(consortium) from the HRA API and accompanying tabular data, and render them
as publication-quality dot graphs and scatter/summary plots.

## Contents

- `datasets-per-organ-per-consortium.ipynb` — Loads dataset graph data from
  the HRA API (`https://apps.humanatlas.io/api/v1/ds-graph`) and a dataset
  list of organs and providers, then produces a dot graph of tissue blocks
  per organ per consortium. Output: `output/datasets-per-organ-per-effort.pdf`.
- `hra-pop-scatter-checkpoint.ipynb` — Reads the per-organ/per-provider count
  table and produces a scatter/summary visualization of organ coverage by
  consortium. Output: `output/organ_consortium_summary.svg`.
- `downloads/` — Cached input data used by the notebooks
  (`datasets-list-organs-providers.csv`,
  `datasets-list-organs-providers-cnt.csv`, and `ds-graph.json`).
- `output/` — Generated figures (PDF, SVG, PNG).

## Requirements

- Python 3.12 (the notebooks were developed and run under Python 3.12.10).
- The third-party Python packages used by the notebooks are listed in
  [`requirements.txt`](requirements.txt): `matplotlib`, `numpy`, `pandas`,
  `requests`, and `seaborn`.

## Installation

```bash
# Clone the repository
git clone https://github.com/cns-iu/hra-cfde-marker-visualizations.git
cd hra-cfde-marker-visualizations

# Create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate        # on Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Install Jupyter to run the notebooks
pip install jupyter
```

## Usage

Launch Jupyter and open either notebook:

```bash
jupyter notebook
# or
jupyter lab
```

Run the cells top to bottom. The first notebook
(`datasets-per-organ-per-consortium.ipynb`) downloads the required source
data into `downloads/` on first run and then writes its figure to
`output/datasets-per-organ-per-effort.pdf`. The second notebook
(`hra-pop-scatter-checkpoint.ipynb`) reads the cached count table from
`downloads/` and writes `output/organ_consortium_summary.svg`.

## Data

Input data is derived from the Human Reference Atlas (HRA):

- The HRA dataset graph API: `https://apps.humanatlas.io/api/v1/ds-graph`
- A dataset list of organs and providers retrieved via the HRA grlc API:
  `https://grlc.io/api-git/hubmapconsortium/ccf-grlc/subdir/hra/datasets-list-organs-providers.csv`

Cached copies of these inputs are stored in `downloads/` so the figures can be
regenerated without re-querying the source services.

## License

This project is licensed under the terms of the MIT License. See the
[`LICENSE`](LICENSE) file for details.
