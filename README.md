# 🏆 Project Proposal: The Impact of Major Sports Events on Sports Video Game Sales

## 🎯 Motivation
The purpose of this project is to investigate whether major international sports events — such as the **FIFA World Cup**, **UEFA European Championship**, and the **Olympic Games** — have a measurable influence on the sales of **sports-related video games**.  

Video game publishers often release or promote new titles around these events (for example, *FIFA World Cup Editions* or *Olympic-themed games*).  
This project aims to determine if there is a **statistically significant increase in sports game sales** during or following these events, and to explore which types of events generate the largest market impact.

By leveraging historical sales and event data, this study seeks to identify consumer behavior trends and provide insights useful for publishers and marketers planning game releases.

---

## 📊 Description of Dataset
The **primary dataset** will be obtained from **Kaggle’s Video Game Sales Dataset (VGChartz)**, which contains detailed sales information for thousands of video games worldwide.  

This dataset includes variables such as:
- **Name**  
- **Platform**  
- **Year of Release**  
- **Genre**  
- **Publisher**  
- **Global, North American, European, and Japanese Sales**

For this project, only games classified under the **“Sports”** genre will be analyzed.

### Derived Features (Feature Engineering)
Additional attributes will be created to better understand the data, such as:
- **Event Year Flag** → Whether the release year coincides with a major sports event.  
- **Years Since Event** → Time difference between release and nearest event year.  
- **Average Regional Share** → Ratio of regional to global sales to detect market preferences.

---

## 🌐 Additional Data Sources
If the Kaggle dataset is incomplete or lacks recent data, it will be enriched with:
- Official lists of **FIFA World Cup**, **UEFA Euro**, and **Olympic Games** years (from Wikipedia or sports data APIs).  
- Potential supplementary data such as **Google Trends** interest levels for keywords like “FIFA,” “Olympics,” and “NBA.”  

These external datasets will allow for time-based correlation between real-world sports events and sales spikes.

---

## 📅 Project Plan

### 1️⃣ Data Collection
- Download and clean the **VGChartz** dataset from Kaggle.  
- Create or import an **events.csv** file listing all major sports events and their corresponding years.  
- Merge both datasets based on release year to label event and non-event periods.

### 2️⃣ Data Processing and Cleaning
- Handle missing or inconsistent values.  
- Convert categorical data (e.g., genre, region) into usable formats.  
- Normalize yearly sales data to adjust for industry growth or inflation.

### 3️⃣ Exploratory Data Analysis (EDA)
- Visualize trends in sports game sales across years and regions.  
- Compare mean sales in event years vs. non-event years.  
- Identify which events (World Cup, Euro, Olympics) align with the largest sales increases.

### 4️⃣ Statistical Testing and Modeling
- Conduct hypothesis testing (t-test or Mann–Whitney U) to verify if sales differ significantly in event years.  
- Build simple regression models to estimate the effect size of event occurrence on sales volume.  
- Evaluate which publishers (EA, Konami, 2K) benefit most from event timing.

---

## 🧩 Hypotheses

### Null Hypothesis (H₀)
> Major sports events have **no significant impact** on the sales of sports video games.

### Alternative Hypothesis (H₁)
> Major sports events lead to a **statistically significant increase** in sports video game sales.

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

