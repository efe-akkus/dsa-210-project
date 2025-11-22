# Project Proposal: The Impact of Chess Openings on Win Rates Across Rating Levels and Time Controls

## Motivation

This project investigates whether different chess openings have a measurable impact on win rates, and how this relationship varies across player rating levels and game types. Chess openings contain early-game plans that structure the rest of the match. Their effectiveness may depend on:

- The skill level of the players (ELO rating)
- The time control of the game (blitz, rapid, classical)
- The strategic or tactical nature of the opening (tactial, positional,agressive, quiet etc.)

Using a large dataset of real games from Lichess, this study aims to determine:

- Which openings lead to higher win rates
- How opening performance differs between blitz, rapid, and classical games
- Whether opening effectiveness changes across player rating groups
- Whether popular openings are also successful
- How ECO opening families behave across formats and skill levels

The goal is to provide a data-driven analysis of how openings influence real game outcomes.

---

## 2. Dataset Description

### Lichess 6.25 Million Games (July 2016)

This project uses a single dataset containing over six million online games.  
Relevant columns include:

- **Opening** — Opening name  
- **ECO** — ECO code  
- **Result** — White win (1-0), Black win (0-1), or draw (1/2-1/2)
- **WhiteElo**, **BlackElo** — Player ratings  
- **game_type** — Blitz, rapid, classical, or bullet  
- **UTCDate**, **UTCTime** — Game timestamp  
- **Termination** — Reason for game ending  
- **AN** — Move list (not used directly)

The dataset already contains all necessary information; no external sources are required.

---

## 3. Data Cleaning and Feature Engineering

### 3.1 Cleaning Procedures
- Remove games missing opening names, ECO codes, or Elo ratings  
- Standardize opening names  
- Convert results into binary labels:
  - `white_win`
  - `black_win`
  - `draw`

### 3.2 Engineered Features
- **Rating Bucket**  
  Based on mean Elo:
  - 800–1200 (Beginner)
  - 1200–1600 (Intermediate)
  - 1600–2000 (Advanced)
  - 2000+ (Expert)

- **Opening Family**  
  Derived from ECO prefix (A, B, C, D, E).

- **Opening Popularity**  
  Frequency of each opening.

- **Game Type**  
  Directly available from dataset.

---

## 4. Exploratory Data Analysis (EDA)

Planned analyses:

### 4.1 Overall Opening Patterns
- Most frequently used openings  
- Highest win-rate openings for White and Black  
- Win-rate visualization across ECO families  
- Popularity versus performance comparisons  

### 4.2 Time Control Comparison
Separate evaluations for:
- Blitz
- Rapid
- Classical

Questions explored:
- Do tactical openings perform better in blitz?
- Do positional openings perform better in classical?
- Are some openings consistent across formats?

### 4.3 Rating-Level Comparison
- Opening effectiveness across rating buckets  
- Identification of openings suited for lower or higher skill levels  

### 4.4 Multi-Dimensional Interaction
Combined analysis of:
