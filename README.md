# qss20-final-project
State Level Scarcity - ACS - NAEP data examination

**Research Questions: Does the relationship between state-level socioeconomic conditions and NAEP math scores differ by certain demographic groups or measurements? Which dimension or demographic is the stronges predictor?**

**Repository Structure**

*code/ :*

Contains 3 notebooks...

-  ***01_data_pull.ipynb -- notebook that processes, pulls, and merges the data together - outputs merged data file***

-  **Takes in:**
  - ACS data: "data/acs_wmath.csv" (from https://github.com/herbertfreeze/QSS20-S26/tree/main/public_data)
  - NAEP API (nationsreportcard.gov) — requires internet access; no API key needed

- What it does:
  - Loads and cleans ACS data (regex column renaming, education bucketing)
  - Pulls NAEP math scores via bulk API requests across 50 states, grades 4 & 8, years 2013–2019
  - Pivots NAEP long → wide; replaces suppression code 999 with NA
  - Left-merges ACS onto NAEP panel on state abbreviation (all 50 states matched)
  - Prints row counts before and after merge as diagnostic

- Outputs:
  - "data/naep_pulled.csv"
  - "data/merged_panel.csv"

-  ***02_visualizations.ipynb -- where data is actually transformed into the visualizations and plots I analyze - outputs all visualizations***

 - **Takes in:**  
- "data/merged_panel.csv" (output of "01_data_pull.ipynb")
- What it does:
  - Produces 5 figures analyzing NAEP math achievement gaps and their relationship to state-level socioeconomic conditions
  - Figure 1: bar chart of score gaps across all demographic variables (income, race, gender, parental education) by grade
  - Figure 2: scatter of state median household income vs. free-lunch score gap with `sns.regplot` regression line and 95% CI band
  - Figure 3: line plot of average male − female NAEP score gap by year and grade
  - Figure 4: male vs. female score trajectories over time with linear trend slopes annotated per line
  - Figure 5: OLS coefficient plot with standardized betas and 95% CIs — which ACS variables best predict state NAEP scores


-  ***03_complete_pipeline.ipynb -- combination of the two prior notebooks condensed into a single place***
 - **Takes in:**
  - ACS data: data/acs_wmath.csv (from https://github.com/herbertfreeze/QSS20-S26/tree/main/public_data)
  - NAEP API (nationsreportcard.gov) — requires internet access; no API key needed
- **What it does:**
  - Runs the full project end-to-end in a single notebook: ACS cleaning → NAEP API pull → pivot and merge → all 5 visualizations
  - Identical logic to 01_data_pull.ipynb and 02_visualizations.ipynb combined
- **Outputs:**
  - data/naep_pulled.csv
  - data/merged_panel.csv
  - all visualizations


*data/ :*

location of data described below (ACS + NAEP)

*output/ :*

Figures created in 02_visualizations: 

Gender_Math_Gap_1.png

Gender_Math_Gap_2.png

Predictors_of_State_Performance.png

Score_Gaps_Demographics.png

State_Wealth_Free_Lunch_Gap.png

**Data Sources**

ACS data - link below and in data/ folder in repo:
https://github.com/herbertfreeze/QSS20-S26/tree/main/public_data

NAEP Data - is pulled via their Data Service API and a CSV of the pull is also in the data/ folder
https://www.nationsreportcard.gov/

Merged Panel - CSV of combined two data sources that is used for most of analysis and visualization

**Order and How to Run**

1. Run 01_data_pull first
2. Run 02_visualizations to generate plots
3. Can run 03_complete_pipeline if needed

**What Figures Show**

*Figure 1: Score Gaps Across Demographic Dimensions*

Every demographic variable pulled from NAEP shows meaningful score gap between binary groups and those gaps widen from 4th to 8th grade.

*Figure 2: State Wealth and Free-Lunch Score Gap*

Wealthier states have larger score gaps between free-lunch eligible and non-eligible students, suggesting higher average income is associated with greater in-state economic stratification in educational outcomes.

*Figure 3: Gender Math Gaps Over Time and Trajectories*

Two figures focused on the same issue. The first shows the male-femal score gap narrowing from 2013-2019. The second shows that both male and female scores declined over this period, but male scores fell faster, explaining the convergence in Figure 3.

*Figure 4: Socioeconomic Predictors of State Math Performance*

OLS regression showing the state's share of college-educated adults is the strongest predictor of NAEP math scores. All other variables held constant.

**End**
