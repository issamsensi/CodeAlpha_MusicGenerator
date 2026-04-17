# CodeAlpha Music Generation

Generate classical-style MIDI music with an LSTM-based notebook pipeline.

This project trains a sequence model on MIDI note/chord tokens, generates new token sequences, exports a MIDI file, and lets you preview audio directly in the notebook.

## Features

- End-to-end workflow in one notebook
- Optional dataset download in notebook (KaggleHub)
- Composer/category filtering (for style-focused training)
- LSTM training with callbacks (checkpointing, early stopping, LR reduction)
- MIDI export and inline audio preview
- Basic dataset exploration and training loss visualization

## Project Structure

```
.
├── generate_music.ipynb
├── requirements.txt
├── .gitignore
└── README.md
```

## Requirements

- Python 3.10+
- pip
- Jupyter Notebook or VS Code Notebook support

Install dependencies:

```bash
pip install -r requirements.txt
```

## Dataset Setup

You have two options:

1. Use the optional KaggleHub download cell in the notebook.
2. Place your local dataset folder as:

```text
music-midi/
```

The notebook automatically uses:

- downloaded path if the `path` variable exists
- otherwise local `music-midi/`

## How To Run

1. Start Jupyter:

```bash
jupyter notebook
```

2. Open `generate_music.ipynb`.
3. Run cells from top to bottom.
4. For quick testing, reduce `EPOCHS` in the setup cell.

## Configuration You Can Tune

In the setup/config cell:

- `CATEGORY_FILTER`:
  - `None` for all composers
  - `['bach']` for one composer
  - `['mozart', 'chopin']` for multiple composers
- `SEQUENCE_LENGTH`
- `EPOCHS`
- `BATCH_SIZE`
- `NUM_GENERATE`
- `TEMPERATURE`

## Outputs

By default, generated files are:

- `best_model.keras`
- `outputs/note_mappings.json`
- `outputs/training_loss_notebook.png`
- `outputs/generated_from_notebook.mid`

These outputs are intentionally ignored by Git via `.gitignore`.

## Notes

- Training can take time depending on dataset size and hardware.
- If your environment has no GPU, use fewer epochs for faster iteration.
- If parsing yields no tokens, verify your dataset path and MIDI file availability.


