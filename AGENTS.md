# AGENTS.md

## Cursor Cloud specific instructions

### What this repo is

Single-purpose **Argoverse 2.0 motion forecasting data exploration** repo: `README.md` plus `argoverse2.0_motion_forecasting.ipynb`. There is no web app, API server, Docker Compose, or pinned dependency manifest in the repo.

### Required runtime

| Component | Purpose |
|-----------|---------|
| Python 3.12+ | Notebook runtime |
| `pandas`, `pyarrow` | Load scenario `.parquet` files |
| `jupyter` / `jupyterlab` | Run the notebook interactively |
| `matplotlib` | Plots from `df.hist()` / `df.boxplot()` in the notebook |

Install (if not already present): `pip install --user pandas pyarrow jupyter matplotlib nbconvert`

Ensure `~/.local/bin` is on `PATH` for `jupyter` commands.

### Data path (important on Linux / Cloud)

The notebook hardcodes a Windows path:

`D:/vectornet/aroverse2.0/train/<scenario_id>/scenario_<scenario_id>.parquet`

On Cloud VMs, either:

1. Download the [Argoverse 2 Motion Forecasting](https://www.argoverse.org/av2.html) dataset and point `parquet_file` at your local path, or
2. Use the sample layout under `/workspace/data/train/...` (generated during environment setup for smoke tests).

There are **no** required environment variables for the notebook itself.

### Running the notebook

```bash
export PATH="$HOME/.local/bin:$PATH"
cd /workspace
jupyter lab --no-browser --ip=127.0.0.1 --port=8888
```

Open `argoverse2.0_motion_forecasting.ipynb` and run all cells after fixing `parquet_file`.

Non-interactive smoke test (patch path in a **copy** only; do not rely on modifying the committed notebook):

```bash
jupyter nbconvert --to notebook --execute /tmp/av2_demo.ipynb
```

### Lint / tests / build

No `requirements.txt`, linter config, test suite, or build step is defined in this repository. Verification is: load a scenario Parquet, explore tracks, and filter the ego (`track_id == 'AV'`) as in the notebook.

### Services

| Service | Required? | Notes |
|---------|-----------|--------|
| Jupyter Lab | Optional (dev UX) | Default port **8888** |
| Database / APIs | No | Not used |
