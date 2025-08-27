# Decoding Trans Legislation: A Python Pipeline for Federal Anti-Trans Bills (2024–2025)

**Decoding Trans Legislation** is a Python-based pipeline and dataset project that addresses a pressing information gap: the lack of accessible, structured data on U.S. federal anti-trans legislation. Built using web scraping and data engineering techniques, this project collects, cleans, and organizes metadata and full-text content for relevant bills introduced in 2024 and 2025.

The goal was to create a centralized, analysis-ready dataset that supports both advocacy and research by making this legislation easier to access, analyze, and visualize.

---

## Key Contributions

### Data Collection via Web Scraping
- Scraped [TransLegislation.com](https://translegislation.com) to retrieve detailed bill information for both years, including:
  - Bill title, caption, description, and policy category
  - Direct links to LegiScan and congress.gov detail pages  
- For 2025, prioritized congress.gov links due to inconsistent LegiScan formatting.

### Structured Data Storage
- Stored scraped content in pandas DataFrames for 2024 and 2025
- Exported to CSVs and merged into a combined dataset (`df_combined`)

### Metadata Extraction & Enrichment
- Used custom Python functions to extract:
  - Congressional session numbers from URLs
  - Bill identifiers (e.g., `HR 10075`)
  - Standardized bill types (e.g., `hr`, `sres`)
- Filled in missing bill types manually where needed

### Full-Text Retrieval & Cleaning
- Constructed XML URLs for each bill using the following pattern:  
  `https://www.congress.gov/{session}/bills/{bill_type}{bill_number}/BILLS-{session}{bill_type}{bill_number}ih.xml`
- Validated and supplemented missing or broken links
- Retrieved and parsed each XML file using BeautifulSoup
- Cleaned full-text content and saved both raw and processed files for future NLP analysis

---

## Potential Users

This project is designed to serve multiple audiences:

- **Journalists & Policy Researchers** – Track patterns in legislative language and momentum over time  
- **Advocates & Community Organizers** – Monitor bill activity and access cleaned full-text versions  
- **Data Scientists & Computational Researchers** – Apply NLP tools like topic modeling and keyword extraction

---

## Files in GitHub Repository

- `tracker_federal.ipynb` – Main pipeline notebook  
- `2024CSV.csv`, `2025CSV.csv`, `df_combined.csv` – Cleaned datasets  
- `Bill_text.txt` – Raw bill XML text  
- `cleaned_text.txt` – Cleaned full-text content  
- `WordCloud.jpg` – Two versions of a word cloud generated from cleaned text:
  - Before stopwords
  - After stopword removal

> 📍 GitHub Repo: [https://github.com/Mcjack1999/GA-Trans-Leg](https://github.com/Mcjack1999/GA-Trans-Leg)

---

## Next Steps

- Align cleaned bill texts with their metadata rows in the dataset  
- Launch Phase 2: Text analysis, such as:
  - Keyword extraction and topic modeling (e.g., NMF, LDA)
  - Comparative visualizations across legislative years
  - Identifying key rhetorical patterns in anti-trans legislative language

---

## Word Cloud Preview

_Example word clouds generated from the cleaned bill text (before and after stopword removal):_

![Word Cloud without Stopwords](WordCloud.jpg)
