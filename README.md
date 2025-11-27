# The Impact of Chess Openings on Win Rates Across Rating Levels and Time Controls

## 1. Motivation

This project investigates whether different chess openings have a measurable impact on win rates, and how this relationship varies across player rating levels and game types. Chess openings represent structured plans for the early phase of the game, and their effectiveness may depend on:

* Player rating (ELO)
* Time control (blitz, rapid, classical)
* Opening style (tactical, positional, aggressive, quiet, etc.)

Using a large dataset of real online games, the project aims to determine:

* Which openings lead to higher win rates
* How opening performance differs across blitz, rapid, and classical formats
* Whether opening effectiveness changes with rating group
* How ECO families behave across categories
* Whether frequently played openings are also strong

The goal is to provide a data-driven assessment of how openings influence actual game outcomes.

---

## 2. Dataset Description

### Lichess 6.25 Million Games (July 2016)

Dataset link:
**[https://www.kaggle.com/datasets/arevel/chess-games](https://www.kaggle.com/datasets/arevel/chess-games)**

Main variables used:

* **Opening** – Opening name
* **ECO** – ECO code
* **Result** – White win, Black win, or draw
* **WhiteElo**, **BlackElo** – Player ratings
* **game_type** – Blitz, rapid, classical, bullet
* **UTCDate**, **UTCTime** – Timestamp
* **Termination** – Ending condition
* **AN** – Move list (not used directly)

The dataset provides complete information for all required analyses.

---

## 3. Data Cleaning and Feature Engineering

### 3.1 Cleaning Steps

* Remove rows with missing:

  * Opening name
  * ECO code
  * WhiteElo or BlackElo
* Normalize opening name strings
* Filter non-standard results
* Convert results into clean binary labels:

  * white_win
  * black_win
  * draw

### 3.2 Feature Engineering

#### Rating Buckets (based on mean Elo)

* 800–1200 → Beginner
* 1200–1600 → Intermediate
* 1600–2000 → Advanced
* 2000+ → Expert

Column added: `rating_bucket`.

#### Opening Family (ECO Prefix)

Derived from ECO codes:

* A – Flank
* B – Semi-open
* C – Open games
* D – Closed games
* E – Indian defenses

Column added: `opening_family`.

#### Opening Popularity

Frequency count per opening or ECO code.

#### Game Type

Used directly for category-level comparisons.

---

## 4. Exploratory Data Analysis (EDA)

### 4.1 Opening Overview

Planned analyses include:

* Most frequently played openings
* Win rates for White and Black by opening
* Comparison of popularity vs win rate
* Heatmaps of ECO family performance

Focus questions:

* Are popular openings also successful?
* Which openings deviate most from expected win-rate baselines?

---

### 4.2 Time Control Comparison

Separate evaluation of:

* Blitz
* Rapid
* Classical

Key questions:

* Do tactical openings perform better in blitz due to faster play?
* Are positional openings more effective in longer formats?
* Are certain openings stable across all time controls?

---

### 4.3 Rating-Level Comparison

Analyses performed for each rating bucket:

* Top-performing openings for each skill group
* Openings that decline or improve with higher rating
* Identification of openings suited for beginners vs experts

This allows detection of openings that require theoretical precision.

---

### 4.4 Multi-Dimensional Interaction

Combined evaluations studying:

* Opening × time control
* Opening × rating
* Opening family × skill level × format

Visualized through grouped bar charts, line plots and heatmaps.

---

## 5. Hypothesis Testing

### H1 — Opening choice influences win rate

**Test:** Chi-square independence test
**Context:** Within same rating bucket and time control

### H2 — Opening effectiveness changes across rating levels

**Test:** Two-proportion z-tests comparing win rates between buckets

### H3 — Opening strength differs across time controls

**Test:** Proportion comparison (e.g., blitz vs rapid, blitz vs classical)

All tests evaluated at 5% and 1% significance levels.

---

## 6. Machine Learning Component

### 6.1 Objective

Predict game outcome using:

* Opening
* ECO family
* Rating difference
* Game type
* Opening popularity

### 6.2 Baseline Models

* Majority class baseline
* Logistic regression using only rating difference

### 6.3 Main Models

* Logistic Regression with encoded openings
* Random Forest Classifier
* Gradient Boosting Classifier

### 6.4 Evaluation Metrics

* Accuracy
* Macro F1 score
* Confusion matrix
* ROC–AUC (binary targets)

Comparison focuses on whether including opening-related features improves prediction over rating-only baselines.

---

## 7. Project Structure

```
/
├── data/
│   ├── raw/                # Original dataset (not committed if large)
│   └── processed/          # Cleaned dataset with features
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_hypothesis_testing.ipynb
│   └── 04_modeling.ipynb
├── figures/
│   └── exported plots
└── README.md
```

The project follows a standard workflow with clear separation of cleaning, EDA, testing, and modeling stages.

---

## 8. Limitations

* Dataset represents online play only
* Some openings have small sample sizes
* Elo rating may not fully reflect player strength
* Termination conditions (e.g., timeout) might bias results
* Opening categories (tactical, positional, etc.) may involve subjective labeling

---

## 9. Future Work

* Add newer datasets to study temporal trends in openings
* Build a dashboard for interactive opening exploration
* Use move-by-move models to measure early-game advantage
* Apply clustering to group openings empirically
* Investigate drawing tendencies and imbalance levels in depth

---

## 10. References

* Lichess Games Dataset (Kaggle)
* ECO Opening Encyclopedia
* DSA 210 course materials on EDA, hypothesis testing, and ML

---

Bu README artık Colab’a atıf içermiyor, örnek projelerle aynı formatta ve doğrudan kullanılabilir.
