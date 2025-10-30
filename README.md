# 🏆 DSA 210 Term Project (2025–2026 Fall)

## 🎯 Title
**Do Major Sports Events Influence Sports Video Game Sales?**

---

## 💡 Motivation
Large international sports events like the **FIFA World Cup**, **UEFA European Championship**, and **Olympic Games** are watched by billions of people and often boost global interest in sports.  
Video game companies frequently release or promote their sports titles around these events (e.g., *FIFA World Cup Editions*, *Mario & Sonic at the Olympics*).  
This project aims to **analyze whether these major sports events have a measurable impact on the sales of sports video games**.

---

## 📊 Data Sources

### 1. **Primary Dataset**
- **Video Game Sales Dataset (VGChartz via Kaggle)**  
  [https://www.kaggle.com/datasets/gregorut/videogamesales](https://www.kaggle.com/datasets/gregorut/videogamesales)  
  - Variables: `Name`, `Platform`, `Year`, `Genre`, `Publisher`, `Global_Sales`, `NA_Sales`, `EU_Sales`, `JP_Sales`.  
  - Only rows with `Genre = 'Sports'` will be used.

### 2. **Enrichment Dataset (Sports Events)**
Custom `sports_events.csv` listing major events:
| Event | Year | Region |
|--------|------|--------|
| FIFA World Cup | 1998, 2002, 2006, 2010, 2014, 2018, 2022 | Global |
| UEFA Euro | 2000, 2004, 2008, 2012, 2016, 2021 | Europe |
| Summer Olympics | 2000, 2004, 2008, 2012, 2016, 2021, 2024 | Global |

Each game year will be compared with nearby event years (`|game_year - event_year| ≤ 1`) to detect possible spikes.

### 3. **Optional Add-ons**
- Inflation/CPI data (World Bank) to adjust for price changes.  
- Google Trends API for keywords like *FIFA*, *Olympics*, *NBA* to estimate public interest.

---

## 🔬 Research Questions / Hypotheses

1. **H₀:** Sports video game sales do *not* change significantly during major sports event years.  
   **H₁:** Sports video game sales *increase* in event years.

2. How strong is the correlation between event timing and global sales?  
3. Do different publishers (EA, Konami, 2K Sports) react differently to these events?  
4. Which event type (World Cup vs Olympics) shows the most impact?

---

## 🧠 Analysis Plan

| Stage | Description |
|--------|-------------|
| **Data Preparation** | Filter sports games, clean missing years, merge with `sports_events.csv` |
| **EDA** | Trend of annual global sales; overlay event years; regional breakdowns |
| **Feature Engineering** | `event_flag`, `years_since_event` features |
| **Hypothesis Testing** | Compare event vs non-event years (t-test or Mann–Whitney U) |
| **Modeling** | Linear Regression or Random Forest predicting `Global_Sales` |
| **Visualization** | Line plots (yearly trend), boxplots (event vs non-event), heatmaps (region × event) |

---

## 📅 Milestones

| Date | Deliverable | Details |
|------|--------------|---------|
| **Oct 31** | GitHub Repo + Proposal (this README) | ✅ |
| **Nov 28** | Data collection + EDA + Hypothesis tests | Raw + cleaned datasets, notebooks |
| **Jan 2** | Modeling + Evaluation | Regression / feature analysis |
| **Jan 9 (23:59)** | Final Submission | Report (.pdf) + notebooks |

---

## ⚙️ Tools & Libraries

```txt
numpy
pandas
matplotlib
seaborn
plotly
scikit-learn
scipy
statsmodels
jupyter

