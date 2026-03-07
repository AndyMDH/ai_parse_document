# Databricks Discharge Summary POC

Companion notebook to the blog post **[ai_parse_document on Databricks SQL Looks Like Magic. Here's What to Solve Before Production.](https://xebia.com/blog/ai-parse-document-on-databricks-sql-looks-like-magic-here-s-what-breaks-in-production/)**

A Bronze → Silver medallion pattern for extracting structured fields from hospital discharge summaries using `ai_parse_document` and `ai_query`. Proof-of-concept, not a production pipeline.

## Requirements
- Databricks Runtime 15.4+
- Unity Catalog
- A model serving endpoint (Claude or GPT-4 class model)

## Getting started
1. Import `notebook.ipynb` into your Databricks workspace
2. Set the three variables in the config cell (`PDF_PATH`, `CATALOG`, `SCHEMA`)
3. Run top to bottom

All PDFs in `data/` are synthetic – no real patient data.

## Author
Andy Ho – [LinkedIn](https://www.linkedin.com/in/andy-h0925/)
