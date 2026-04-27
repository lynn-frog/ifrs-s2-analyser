# IFRS S2 Gap Analyser — Setup & Run Guide

## What it does
Upload any company's annual report (PDF) and the tool will:
1. Extract all text from the report
2. Run AI analysis across all **92 IFRS S2 requirements** in 4 categories
3. Return a colour-coded Excel report showing Yes / Partial / No for each requirement, with page citations, materiality ratings, and improvement recommendations

---

## Prerequisites
- Python 3.9 or higher
- An **Anthropic API key** (get one at https://console.anthropic.com)

---

## Installation

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Run the app
streamlit run app.py
```

The app will open automatically in your browser at http://localhost:8501

---

## Usage
1. Enter your **Anthropic API key** in the sidebar
2. Enter the **company name** (e.g. "BHP Group")
3. Upload the **annual report PDF**
4. Click **Run IFRS S2 Analysis**
5. Wait ~2–4 minutes while the AI analyses all 4 categories
6. Download the **Excel report** with full gap analysis

---

## Output Excel Structure

| Sheet | Contents |
|-------|----------|
| **Summary** | Overall stats (Yes/Partial/No counts) + per-category breakdown |
| **Benchmark Analysis** | All 92 requirements with fulfillment status, disclosure summary, page numbers, materiality, and recommendations |

### Columns in Benchmark Analysis
1. **IFRS S2 Disclosure Requirement** — name of the requirement
2. **Fulfillment Status** — Yes / Partial / No (colour-coded green/yellow/red)
3. **Disclosure Summary** — what the company disclosed (or didn't)
4. **Page Number(s)** — specific pages where evidence was found
5. **Materiality (Sector-Relevant)** — Very High / High / Moderate / Low / Very Low
6. **Recommended Enhancements** — specific, actionable improvements
7. **Applicable Scope** — IFRS S2 paragraph reference
8. **Type** — Qualitative / Quantitative
9. **Category** — Governance / Strategy / Risk Management / Metrics & Targets

---

## Notes
- Analysis makes **4 API calls** (one per category) — typical cost ~$1–3 per report
- Very long reports (500+ pages) are automatically truncated to ~120,000 characters
- The model used is **claude-opus-4-5** for maximum analytical depth
