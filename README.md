# Vector DB lab

Each engine lives in its own folder so notebooks, local files, and dependencies stay separate.

```text
.
├── sqlite/          # SQLite BLOBs + NumPy distance (local file DB)
├── chroma/          # Chroma (local persist under data/)
├── pinecone/        # Pinecone (hosted; API key in .env)
├── annoy/           # Spotify Annoy (index files under data/)
└── README.md
```

Inside every engine folder:

```text
<engine>/
  notebooks/         # experiments for this DB only
  data/              # local indexes / persist dirs (gitignored)
  requirements.txt   # pip packages for this DB only
```

## How to work

1. Open the notebook under the engine you are trying (`sqlite/notebooks/01_basics.ipynb`, etc.).
2. Create a venv if you want isolation: `python -m venv .venv && source .venv/bin/activate`.
3. Install **that engine’s** requirements, not a mix of all of them:

   ```bash
   pip install -r sqlite/requirements.txt
   ```

4. Keep generated files in that engine’s `data/` directory.

Add another engine the same way: new folder, `notebooks/`, `data/`, `requirements.txt`.

## Engines

| Folder | What it is | Data lives |
|---|---|---|
| `sqlite/` | SQLite + NumPy (this lab’s first notebook) | `sqlite/data/*.db` |
| `chroma/` | Chroma collections | `chroma/data/` persist path |
| `pinecone/` | Hosted index | Cloud; put `PINECONE_API_KEY` in `.env` |
| `annoy/` | Approximate nearest neighbors | `annoy/data/*.ann` |
