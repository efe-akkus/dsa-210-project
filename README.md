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

A series of exploratory visualizations were generated to understand the structure of the data before formal hypothesis testing. The EDA focuses on rating distributions, time-control patterns, opening family behavior, and the relationship between openings and win rates.

### **4.1 Player & Game Distributions**

Several baseline distributions were examined to understand the composition of the dataset:

* **Rating bucket distribution** (Beginner, Intermediate, Advanced, Expert)
* **Event type distribution** (blitz, bullet, rapid, classical)
* **Opening family frequency** (A–E)
* **Overall result distribution** (white, black, draw)

These provide context for interpreting opening performance across different subsets of players and game formats.

---

### **4.2 Opening Performance Patterns**

To investigate opening effectiveness, the following visual analyses were performed:

* **White win rate by opening family**
* **Opening family distribution across rating buckets**
* **White win rate heatmaps**

  * Rating bucket × Opening family
  * Event type × Opening family
* **Draw-rate differences** across time controls

These plots reveal how opening families behave under different conditions and whether certain styles favor specific skill levels or formats.

---

### **4.3 Relationships Between Openings & Performance**

Additional analyses explore performance variation at a more granular level:

* **Opening popularity vs white win rate** (log-scaled scatter plot)
* **Elo difference vs white win probability** (binned curve)

These visualizations help identify whether popular openings tend to perform better, and how opening choice interacts with rating advantages.

---

### **4.4 Multi-Dimensional Interaction Effects**

To understand the combined influence of rating, time control, and opening family, multidimensional views were generated:

* Opening family compositions across rating buckets
* Opening family compositions across event types
* Interaction heatmaps that summarize the joint effects of:

  * Opening × Rating
  * Opening × Time Control

These analyses will guide the statistical hypothesis testing performed later.

---

## 5. Hypothesis Testing

### **H1 — Opening choice influences win rate**

**Null Hypothesis (H₀)**
Opening choice does not affect win rates when rating level and time control are held constant. Win-rate differences between openings are due to random variation.

**Alternative Hypothesis (H₁)**
Opening choice has a significant effect on win rates within the same rating level and time control.


### **H2 — Opening effectiveness changes across rating levels**

**Null Hypothesis (H₀)**
The win rate of a given opening is the same across all rating buckets. Rating level does not modify opening effectiveness.

**Alternative Hypothesis (H₁)**
The win rate of a given opening differs across rating buckets. Rating level modifies the effectiveness of openings.


### **H3 — Opening strength differs across time controls**

**Null Hypothesis (H₀)**
An opening’s win rate is identical across blitz, rapid, and classical formats. Time control has no effect on opening performance.

**Alternative Hypothesis (H₁)**
An opening’s win rate changes across blitz, rapid, and classical formats. Time control influences opening performance.

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

### 7. Limitations

Data represents online games only; results may not generalize to over-the-board play.
Rare openings have small sample sizes, which can distort win-rate estimates.
Elo ratings are imperfect measures of true player skill.
Timeouts and resignations can influence results independent of opening choice.
ECO families are broad and do not capture detailed stylistic differences.

---

### 8. Future Work

Include move-level evaluations or engine analysis for deeper opening strength assessment.
Extend the dataset to additional years or platforms to reduce sampling bias.
Build empirical opening-style clusters instead of relying on ECO families.
Add interpretability tools (feature importance, SHAP) to understand model behavior.
Create an interactive dashboard to explore openings across rating levels and formats.
