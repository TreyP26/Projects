# Tommy John Project Overview

This project investigates the relationship between Tommy John surgery (ulnar collateral ligament injury) and pitcher pitch characteristics in Major League Baseball. Specifically, it examines whether velocity and spin rate across different pitch types are associated with an increased likelihood of undergoing Tommy John surgery.

The motivation behind this analysis is to better understand how modern pitching trends—such as increased velocity and spin—may relate to arm injuries. As pitchers continue to push physical limits, identifying statistical relationships between pitch metrics and injury history can provide insight for teams, analysts, and player development staff.

## Research Question

Are pitch velocity and spin rate associated with the occurrence of Tommy John surgery, and does this relationship differ by pitch type?

## Pitch characteristics examined in this project include:

- Fastball velocity
- Breaking ball velocity
- Off-speed pitch velocity
- Fastball spin rate
- Breaking ball spin rate
- Off-speed pitch spin rate

## Data Description

The dataset consists of MLB pitch-level tracking data aggregated to the pitcher–season level. Each observation represents a single pitcher in a given season and includes summary statistics for pitch velocity and spin rate by pitch category.

Pitchers were labeled based on Tommy John surgery status using publicly available injury and surgery records. This allowed for comparisons between pitchers who have undergone the procedure and those who have not.

## Pitch Classification

Individual pitch types were grouped into three broad categories:

Fastballs (e.g., four-seam, two-seam, sinkers)
Breaking balls (e.g., sliders, curveballs)
Off-speed pitches (e.g., changeups, splitters)

This grouping reduces noise from pitch-type granularity and allows for clearer interpretation of results.

## Data Sources

This project combines pitch-tracking and injury data from multiple public baseball analytics sources:

Baseball Savant – pitch-level Statcast data, including pitch velocity and spin rate
FanGraphs – supplemental pitching metrics and player information
ESPN – publicly reported injury and surgery histories used to identify Tommy John surgery

These sources were merged to create a pitcher–season level dataset containing both performance metrics and injury indicators.

## Data Preparation

Significant preprocessing was required to align pitch-tracking data with injury records across multiple data sources.

### Name Standardization and Merging

Player names appeared in inconsistent formats across datasets (e.g., "Last, First" vs. "First Last"). To ensure accurate joins:

Player names were normalized by:
Removing punctuation and whitespace
Converting all text to lowercase
Reformatting comma-separated names into a consistent structure
A cleaned name field was created in both the pitch data and injury data and used as the merge key.

### Pitch-level performance data were then merged with injury records using this standardized identifier.

- Injury Labeling
- Injury descriptions were scanned for mentions of “Tommy John” surgery.
- A binary indicator (HadTommyJohn) was created:
  - 1 if a pitcher had undergone Tommy John surgery 0 otherwise
- Missing injury records were treated as no documented Tommy John surgery.

### Feature Construction

Pitch-level data were aggregated to the pitcher–season level and grouped into three pitch categories:

- Fastballs
- Breaking balls
- Off-speed pitches

For each pitcher-season and pitch category, the following features were computed:

- Average pitch velocity
- Average spin rate
- Total pitch count (used for filtering reliability)

Only pitchers with sufficient pitch counts were retained to reduce noise from small samples.

### Final Dataset

The final modeling dataset includes:

- Pitcher name and season
- Pitch counts by pitch category
- Average velocity and spin rate for each pitch category
- Binary Tommy John surgery indicator

This cleaned and merged dataset forms the basis for all subsequent exploratory analysis and correlation modeling.

## Methodology

This analysis focuses on identifying associations, not causal relationships, between pitch characteristics and Tommy John surgery.

### Analytical Approach
- Correlation analysis was used to measure the strength and direction of the relationship between Tommy John surgery status and each velocity and spin rate metric.
- Correlations were evaluated separately for fastballs, breaking balls, and off-speed pitches to determine whether injury associations differ by pitch type.
- Exploratory visualizations (such as scatterplots and correlation matrices) were used to identify trends, outliers, and potential nonlinear patterns.
### Assumptions and Scope
- The analysis does not imply causation; higher velocity or spin rate does not necessarily cause injury.
- Injury timing, pitching workload, biomechanics, rest patterns, and prior injuries were not explicitly modeled.
- Tommy John surgery was treated as a static outcome rather than a time-to-event process.

## Results 
<img width="1000" height="615" alt="Off-Speed_TJ_Velo" src="https://github.com/user-attachments/assets/6072392f-7010-4bb0-bb91-1e6b20599d28" />  

<img width="1000" height="615" alt="Breaking_Ball_TJ_Velo" src="https://github.com/user-attachments/assets/0d64e05b-7865-4189-af14-67dd135b4212" />

<img width="1000" height="615" alt="Fastball_TJ_Velo" src="https://github.com/user-attachments/assets/2d1badd0-626c-47a5-bbfd-e5c3f23a3429" />

<img width="1000" height="615" alt="Off-Speed_TJ_Spin" src="https://github.com/user-attachments/assets/c166a74f-e702-4534-ae2d-5165b54d8bcc" />

<img width="1000" height="615" alt="Breaking_Ball_TJ_Spin" src="https://github.com/user-attachments/assets/4a40e296-ffe1-4245-a1c7-ff924b571320" />

<img width="1000" height="615" alt="Fastball_TJ_Spin" src="https://github.com/user-attachments/assets/4c131a4f-a1b1-44d7-b6c5-5544881aa08f" />

<img width="1000" height="615" alt="Pitches_TJ" src="https://github.com/user-attachments/assets/59f819af-2075-484e-9961-fc1c38884345" />

