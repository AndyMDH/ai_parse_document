# The Hidden Cost of ai_parse_document in Production

Companion notebook for the blog post **[The Hidden Cost of ai_parse_document in Production](https://xebia.com/blog/hidden-cost-ai-parse-document-production-databricks/)**.

A Bronze → Silver medallion pattern for extracting structured fields from hospital discharge summaries using `ai_parse_document` and `ai_query`. Demonstrates the gap between a proof-of-concept query and a production-ready pipeline: deduplication, streaming checkpoints, prompt versioning, pseudonymisation, and noise stripping.

This is a proof-of-concept, not a production pipeline.

## Repository structure

```
.
├── document_parsing_pipeline.ipynb   # Main notebook — run this
└── data/
    └── discharge_pdfs.zip      # Synthetic discharge summaries (no real patient data)
```

> **Note:** The sample set here is scanned/OCR documents only. The "digitally-born vs. scanned" comparison and `_digital.pdf` filenames in the blog post are illustrative of the pattern, not files included in this zip.

## Requirements

- Databricks Runtime 17.1+
- Unity Catalog
- A model serving endpoint (`databricks-claude-sonnet-4` or equivalent)

## Getting started

1. Extract `data/discharge_pdfs.zip` to a UC Volume or Workspace folder
2. Import `document_parsing_pipeline.ipynb` into your Databricks workspace
3. Set the four variables in the config cell:
   - `PDF_PATH` — path to the extracted PDFs
   - `CATALOG` — your Unity Catalog name
   - `SCHEMA` — target schema
   - `MODEL_ENDPOINT` — your model serving endpoint name
4. Run top to bottom

The batch cells are illustrative. The Structured Streaming cells (Bronze: Task 1–3) are the recommended production path — they use Auto Loader checkpoints so only new files are processed on each run.

## Author

Andy Ho — [LinkedIn](https://www.linkedin.com/in/andy-h0925/)
