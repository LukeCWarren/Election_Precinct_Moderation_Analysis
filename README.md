# Election_Precinct_Moderation_Analysis
# LD22 Moderate Precinct Analysis

## Overview

This project analyzes election results in **Washington Legislative District 22 (LD22)** to identify precincts where a *moderate candidate* would have the strongest opportunity to gain votes.

The notebook compares **2022 midterm** and **2024 presidential-year** results for:

* Representative Position 1
* Representative Position 2

It then computes a custom **Opportunity Score** to rank precincts by persuasion potential rather than partisan strength.

---

## Goal

Identify precincts where:

* Voters show flexibility or mixed voting patterns
* Margins are competitive
* Incumbent support weakened
* Landslides are absent

These precincts are ideal targets for outreach, persuasion, or campaigning.

---

## Data Source

`ld22_election_data.csv`

Contains:

* Precinct-level vote totals
* Candidate names
* Party labels
* Election year
* Registered voters
* Ballots cast

Filtered to:

* Legislative District 22 only
* Years: 2022 and 2024
* Contests: Rep Position 1 & Rep Position 2

---

## Methodology

### District Baseline Comparison

The script first computes districtwide vote shares for each race and year to establish baseline performance.

This allows precinct-level results to be evaluated relative to district norms instead of raw vote totals.

---

### Opportunity Score Algorithm

Each precinct receives a composite score based on four weighted factors:

| Factor                | Weight | Rationale                                            |
| --------------------- | ------ | ---------------------------------------------------- |
| Closeness             | ×2.0   | Competitive races indicate persuadable voters        |
| Incumbent Weakness    | ×1.5   | Decline in incumbent performance suggests openness   |
| Split-Ticket Behavior | ×1.2   | Variation across races implies candidate sensitivity |
| Turnout Potential     | ×1.0   | Lower turnout precincts offer growth potential       |

Higher scores = better opportunity targets.

---

### Additional Filters

Precincts are prioritized if they meet behavioral criteria:

* Underperform district baseline for major parties
* No candidate exceeds ~58% vote share
* Margin bands indicate competitiveness

---

## Output

The notebook generates:

**1. Charts**

* District results comparison (2022 vs 2024)
* Ranked top precincts visualization

**2. Ranked Dataset**

```
ld22_opportunity_rankings.csv
```

Contains:

* Precinct name
* Opportunity score
* Tier classification
* Vote margins
* Swing metrics
* Context variables

---

## Tier Definitions

Precincts are grouped for strategy prioritization:

| Tier              | Meaning                      |
| ----------------- | ---------------------------- |
| TIER 1 – TOP      | Highest persuasion potential |
| TIER 2 – HIGH     | Strong targets               |
| TIER 3 – MODERATE | Worth monitoring             |
| Lower tiers       | Low strategic value          |

---

## How to Run

### Requirements

Install dependencies:

```
pip install pandas numpy matplotlib
```

### Execute Notebook

Run all cells in:

```
ld22_moderate_precincts_analysis.ipynb
```

Ensure the CSV file is in the same directory.

---

## File Structure

```
project/
│
├── ld22_moderate_precincts_analysis.ipynb
├── ld22_election_data.csv
└── ld22_opportunity_rankings.csv (generated)
```

---

## Interpretation Notes

This analysis intentionally:

* Uses **behavioral voting patterns**, not demographics
* Focuses on persuasion potential, not party dominance
* Treats split-ticket behavior as evidence of candidate openness

This makes it useful for:

* Campaign targeting
* Field strategy
* Messaging experiments
* Political data exploration projects

---

## Possible Extensions

Future improvements could include:

* Incorporating turnout history trends
* Adding statewide race comparisons
* Modeling probability of vote shift
* GIS mapping of opportunity clusters
* Machine learning ranking models

---

## License / Use

This project is intended for research, educational, or analytical use.
Verify election data accuracy before making real-world decisions.

---

**Author:** Luke Warren
**Project Type:** Political Data Analysis / Strategy Analytics
