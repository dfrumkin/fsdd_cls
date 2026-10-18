# FSDD audio classification

Spoken digit classification on the
[Free Spoken Digit Dataset](https://github.com/Jakobovski/free-spoken-digit-dataset)
(FSDD) with PyTorch, torchaudio, NumPy and scikit-learn.

## Setup

Requires [uv](https://docs.astral.sh/uv/).

```bash
uv sync
```

This creates `.venv/` with Python 3.13 and the dependencies pinned in `uv.lock`.

## Dataset

FSDD is a git submodule at `data/free-spoken-digit-dataset`, pinned to a
specific commit. Clone with `git clone --recurse-submodules`, or, in an
existing clone, run:

```bash
git submodule update --init
```

Recordings are in `data/free-spoken-digit-dataset/recordings/`: 3,000 mono
8 kHz WAV files named `{digit}_{speaker}_{index}.wav`.

## Jupyter in VSCode

Open a notebook and select the `.venv` interpreter (Python 3.13) as the kernel.

## Loading audio

Load WAV files with `soundfile`, not `torchaudio.load` (it requires TorchCodec
and system FFmpeg, which are not installed). Use torchaudio for transforms
such as `MelSpectrogram` and `MFCC`.
