# qss20-final-project
State Level Scarcity - ACS - NAEP data examination

**Research Questions: Does the relationship between state-level socioeconomic conditions and NAEP math scores differ by certain demographic groups or measurements? Which dimension or demographic is the stronges predictor?**

**Repository Structure**

*code/ :*

Contains 3 notebooks...

-  01_data_pull.ipynb -- notebook that processes, pulls, and merges the data together - outputs merged data file

-  02_visualizations.ipynb -- where data is actually transformed into the visualizations and plots I analyze - outputs all visualizations

-  03_complete_pipeline -- combination of the two prior notebooks condensed into a single place

*data/ :*

location of data described below (ACS + NAEP)

*output/ :*

Figures created in 02_visualizations

**Data Sources**

ACS data - link below and in data/ folder in repo:
https://github.com/herbertfreeze/QSS20-S26/tree/main/public_data

NAEP Data - is pulled via their Data Service API and a CSV of the pull is also in the data/ folder
https://www.nationsreportcard.gov/

Merged Panel - CSV of combined two data sources that is used for most of analysis and visualization

**How to Run**

1. Run 01_data_pull first
2. Run 02_visualizations to generate plots
3. Can run complete pipeline if needed

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
