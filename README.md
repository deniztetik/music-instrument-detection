Based off of this notebook https://www.kaggle.com/code/dima806/musical-instrument-detection

## Preserved project state (2026-10-05)

This checkout was restored from `deniztetik/music-instrument-detection` before
removing an old local dependency environment to reclaim disk space. The notebook,
original `Pipfile` / `Pipfile.lock`, and previously committed MLflow records remain.
No original local project directory was present when this checkout was restored.

`requirements-local-py312.txt` records the installed package versions from the
local environment created in May 2024. That environment used CPython 3.12.3,
PyTorch 2.3.0, torchaudio 2.3.0, and NVIDIA CUDA 12 packages. The original Pipfile
instead requests Python 3.11.9; its lockfile is retained unchanged. These are two
different historical environment records, not interchangeable lockfiles.

Before removal, 29,444 installed files with package-provided checksums were
checked. None differed from its recorded checksum; the only unrecorded files in
site-packages were standard virtualenv bootstrap files. No editable source
checkout was present in the environment's `src` directory.

### Picking up the project again

To attempt rebuilding the observed local environment with Python 3.12:

```sh
python3.12 -m venv .venv
. .venv/bin/activate
python -m pip install -r requirements-local-py312.txt
```

Alternatively, use Python 3.11.9 and `pipenv sync --dev` to reconstruct the original
Pipfile.lock environment. Neither reconstruction nor training was tested during
this storage cleanup. Availability of historical package versions, platform/GPU
compatibility, and notebook behavior still need checking when resuming.

The notebook expects external audio data in `downloads/`, including
`Metadata_Train.csv`, `Metadata_Test.csv`, and the Train/Test submission WAV
folders. Those data files and trained model weights were not found or recovered
by this cleanup. Restore/download the data separately before running training.

Review the notebook's setup cells before running: they contain historical package
pins and system package installation commands. Its example inference paths are
Kaggle-specific. The final cells authenticate to Hugging Face and upload a model
to the original notebook author's namespace; change that destination to your own
before deliberately publishing a model. Credentials must remain outside Git.

Keep downloaded data, virtual environments, model checkpoints, and new experiment
outputs outside version control. Removing the local environment does not remove
the source notebook or the dependency records needed to investigate a restart.
