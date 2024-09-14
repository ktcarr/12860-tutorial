# Assignment 1: model validation

Imagine you've been tasked with making a regional climate change projection based on output from a global climate model (for example, perhaps the Boston city council is interested in the risk of flooding 30 years in the future). Before looking at the model's projected changes, we need to evaluate how well the model simulates the current climate. This is what we'll do in this assignment (we'll get to the projected changes later on in the course).

In particular, you're going to valid the CESM2 climate model's ability to represent regional climate variability. You'll start by choosing a region and variable (e.g., the same as from class on 9/19). Then you'll compute statistics for the region/variable in both a reanalysis product and the CESM2 climate model. Finally, you'll compare the statistics and assess the model's performance. Detailed instructions and a grading rubric are below.

## Part 0: Choose a region, a variable, and an "index" (1 pt)
The "index" should be a scalar metric which can be evaluated at every timestep. For example, this could be the temperature at a given location or averaged over a given region.


## Part 1: Compute statistics for the reanalysis (1.5 pts)
Some possible diagnostic plots:
- spatial plots of mean, variance
- line/bar plot of index's seasonal cycle (e.g., showing mean and variance for each month)
- histogram of index anomalies (Does the distribution look normal?)
- spatial plot showing correlation between your index and data at each gridpoint
- power spectral density of the index


## Part 2: Compute statistics for CESM2 (1.5 pts)
Make the same plots, but for model output from CESM2 instead of the reanalysis.


## Part 3: Compare the statistics (3 pts)
Create a few diagnostic plots of the model's performance.
The goal is to evaluate how well the model's statistics match those of the reanalysis.
Some ideas:
- "difference" plots (e.g., difference between model and reanalysis mean/variance at every gridpoint)
- overlay index statistics from each data product on the same plot (e.g., seasonal cycle, histogram, power spectral density)


## Part 4: Assess the model's performance (3 pts)
- What's your overall impression of the model's performance?
- How well does it represent the statistics of your index?
- Would the model do a better job if you modified your index (e.g., increased the area for spatial averaging, or looked at annual rather than monthly averages?).
