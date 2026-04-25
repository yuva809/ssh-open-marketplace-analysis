# SSH Open Marketplace – Catalogue Analysis

**DARIAH ERIC | Research Software Engineer Technical Assessment – Option C**

---

## Overview

This notebook explores the [SSH Open Marketplace](https://marketplace.sshopencloud.eu/) — a discovery portal for tools, services, training materials, datasets, publications, and workflows in the Social Sciences and Humanities.

The analysis uses the Marketplace's public REST API (`https://marketplace-api.sshopencloud.eu/api`) to fetch real data and answer five questions about the catalogue's content and quality.

---

## Questions Addressed

| # | Question |
|---|----------|
| 1 | How are item types distributed across the catalogue? |
| 2 | How consistently are key metadata fields populated? |
| 3 | Which controlled vocabularies are used and which concepts are most common? |
| 4 | Which data sources contribute the most items? |
| 5 | How recently have items been updated? |

---

## Key Findings

- **Tool or Service** is the largest category with 2,691 items (44.7% of the catalogue)
- `label`, `description`, and `source` are well-populated across all types; `externalIds` and `relatedItems` are consistently sparse
- **TaDiRAH 2** is the dominant research activity vocabulary; *Analyzing* is the most common concept
- Just **287 concepts** (out of 933 distinct ones) account for 80% of all annotations — indicating a long tail of rarely-used concepts
- **72% of sampled items** were last updated in 2024 or later, suggesting an actively maintained catalogue
- The Workflows endpoint consistently timed out during testing — noted in the reflection section

---

## How to Run

**1. Install dependencies**
```bash
pip install requests pandas matplotlib seaborn notebook
```

**2. Launch Jupyter**
```bash
jupyter notebook ssh_marketplace_analysis.ipynb
```

**3. Run all cells**
`Cell → Run All`

The notebook fetches live data from the API — expect ~8 minutes for full execution.

---

## Requirements

```
requests>=2.31.0
pandas>=2.0.0
matplotlib>=3.7.0
seaborn>=0.12.0
notebook>=7.0.0
```

---

## Notes

- The Swagger UI link provided in the task brief (`/api/swagger-ui.html`) returned a 404. The API itself is fully functional — I explored the live endpoint responses directly to understand the schema.
- All requests include a 0.5 second delay between pages to avoid overloading the server.
- No write operations are performed — the notebook is read-only.
