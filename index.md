---
title: Mapping State Legislative District Competitiveness with PVI
layout: single
author_profile: true
toc: true
toc_depth: 2
---
<style>
.page__content {
  font-size: 0.8em;
  line-height: 1.6;
}
</style>

> The complete code notebooks, data processing scripts, and source files for this project are available in the [project repository](https://github.com/samforwill/sldu-piv). 


The initial goal of this project was to demonstrate my capabilities in manipulating shapefiles with geopandas and producing maps with QGIS. However, as I got into the weeds, I fell into my own rabbit-hole taking a deeper dive into the competitiveness of state legislative districts, complemented by some pretty cool maps! #GIS

This project used an ML model trained on demographic characteristics of Congressional Districts to predict Partisan Voter Index (PVI) scores. This model's predictive accuracy with PVI on Congressional Districts had an R^2 of 0.92 and RMSE of 4.3. Using this pre-trained model, PVI scores were assigned to every state legislative district's upper chamber/state senate seats based on the same demographic features.

## Project Steps

1. **Model Training and Prediction**:
    - Trained a model to predict PVI scores for Congressional districts.
    - Applied the model to predict PVI for state senate districts.

2. **Evaluation and Adjustment**:
    - Initially, the model predicted 31% of Senate seats in the US were held by Democrats, but the actual composition of total Dem seats in the US was 42%.
    - Determined there was a systematic undervaluation of Democrats in state legislative races in every state.
    - Assumed the electorate in low-turnout elections behaved more Democratic than in Presidential elections, so assigned a 6.25-point shift towards Dems in Partisan scores to each state legilsative district to align predictions with actual composition in the US.

3. **State-by-State Analysis**:
    - Post-adjustment, the model showed improved predictions for state legislative compositions across nearly all states except New Hampshire (NH Partisan scores are nearly all within the "tossup" or "tilt" zone).

4. **Detailed Case Study - North Carolina**:
    - Conducted a detailed analysis of North Carolina's state senate seats using QGIS.
    - Mapped and colored districts based on predicted and actual party control. Adjusted model mispredicted only 5 out of 50 districts, and each of those districts was a tossup or tilt district (one of which was a Democrat (Sydney Batch, NC-17) in a predicted Republican district who was appointed to the seat by the Democratic Governor, Roy Cooper).

5. **Visualization of Predictive Power**:
    - Generated maps for all state legislative seats in the USA, categorizing districts from "Super Solid D" to "Super Solid R".

I am currently working on a more detailed write-up for this project with interactive maps. In the meantime, check out the visualizations:

## Visualizations

1. [![Predicted Composition Donut](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/1-%20Predicted%20Composition%20Donut.png)](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/1-%20Predicted%20Composition%20Donut.png){:target="_blank" rel="noopener"}

2. [![Predicted Composition State Senates](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/2-%20Predicted%20Composition%20State%20Senates.png)](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/2-%20Predicted%20Composition%20State%20Senates.png){:target="_blank" rel="noopener"}

3. [![Shifted Predicted Composition Donut](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/3-%20Shifted%20Predicted%20Composition%20Donut.png)](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/3-%20Shifted%20Predicted%20Composition%20Donut.png){:target="_blank" rel="noopener"}

4. [![Shifted Predicted Composition State Senates](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/4-%20Shifted%20Predicted%20Composition%20State%20Senates.png)](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/4-%20Shifted%20Predicted%20Composition%20State%20Senates.png){:target="_blank" rel="noopener"}

5. [![Composition Error](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/5-%20Composition%20Error.png)](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/5-%20Composition%20Error.png){:target="_blank" rel="noopener"}

6. [![USA PVI](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/6-%20USA%20PVI.png)](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/6-%20USA%20PVI.png){:target="_blank" rel="noopener"}

7. [![NC Senate Seats](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/7-%20NC%20Senate%20Seats.png)](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/7-%20NC%20Senate%20Seats.png){:target="_blank" rel="noopener"}

8. [![GOP Gerrymander](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/8-%20GOP%20Gerrymander.png)](https://raw.githubusercontent.com/samforwill/State-Legislative-Districts-PVI/main/images/8-%20GOP%20Gerrymander.png){:target="_blank" rel="noopener"}


Stay tuned for more updates and interactive versions of these maps!
