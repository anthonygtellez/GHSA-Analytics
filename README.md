# 🛡️ GitHub Security Advisory Database Analyzer

An interactive Google Colab notebook that analyzes the [GitHub Security Advisory Database](https://github.com/github/advisory-database), enriched with CISA's Known Exploited Vulnerabilities (KEV) catalog and NLP-powered clustering.

---

## 🔍 What This Project Does

- Parses all GitHub-reviewed advisories and preserves full advisory metadata including:
  - Affected package versions
  - CVEs, CWE IDs, references
  - Publication and modification dates
- Enriches advisories with:
  - Ecosystem (npm, PyPI, Maven, etc.)
  - Package name
  - Severity level (LOW, MODERATE, HIGH, CRITICAL)
  - CISA KEV status
- Saves each severity level to:
  - Full `.json` files with original and enriched fields
  - Flattened `.parquet` files for analysis and plotting
- Visualizes risky software and trends using:
  - Interactive Plotly scatterplots
  - UMAP-based 2D clustering of NLP summaries to identify similar vulnerabilities

---

## 🚀 How to Use the Notebook

1. **Open in Google Colab**

   Upload the notebook or open it directly via:
   ```
   File > Upload Notebook > Select `Github_Security_Advisory_Database.ipynb`
   ```

2. **Run all cells**

   From the Colab menu:
   ```
   Runtime > Run all
   ```

3. **Explore the Outputs**

   - Parquet and JSON files saved in `parsed_advisories/`
   - UMAP plots cluster similar CVEs by text
   - Filter by ecosystem, package, or KEV status to prioritize threats

---

## 🧠 Advanced Analysis (Optional)

- Use `sentence-transformers` to generate summary embeddings
- Use `umap-learn` to visualize clusters of semantically similar advisories
- Export filtered data to CSV or visualize in external BI tools

---

## 🔬 Requirements (Handled Automatically in Colab)

- `umap-learn`
- `sentence-transformers`
- `plotly`
- `pandas`
- `pyarrow`
- `huggingface_hub` (optional for login)

---

## 🔐 Hugging Face Access (Optional)

Some NLP models require Hugging Face authentication.

### Option 1: Login from notebook
```python
from huggingface_hub import login
login()
```

### Option 2: Use Colab Secret Manager
Store your token as `HF_TOKEN`:
```python
import os
from huggingface_hub import login
login(token=os.environ["HF_TOKEN"])
```

---

## 📊 Visualization Features

- Bubble/scatter plots of vulnerable packages by ecosystem and severity
- Cluster view of CVEs grouped by NLP similarity
- Easily identify critical packages or commonly exploited components

---

## 🤝 Credits

- GitHub [advisory-database](https://github.com/github/advisory-database)
- CISA [Known Exploited Vulnerabilities Catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)
- Hugging Face `sentence-transformers`
- Plotly + UMAP for clustering

---

## 📄 License

MIT License — feel free to modify and adapt this notebook for your security team or research. Happy Hunting [@anthonygtellez](anthonygtellez.github.io)
