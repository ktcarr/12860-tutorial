# Assignment 1: model validation

Imagine you've been tasked with making a regional climate change projection based on output from a global climate model (for example, perhaps the Boston city council is interested in the risk of flooding 30 years in the future). Before looking at the model's projected changes, we need to evaluate how well the model simulates the current climate. This is what we'll do in this assignment (we'll get to the projected changes later on in the course).

In particular, you're going to valid the CESM2 climate model's ability to represent regional climate variability. You'll start by choosing a region and defining a climate index for that region (you already did this part if you came to class on 9/19!). Then you'll compute statistics for the region/variable in both a reanalysis product and the CESM2 climate model. Finally, you'll compare the statistics and assess the model's performance. Detailed instructions and a grading rubric are below.

## 1) Choose a region and a climate "index" (2 pts)
Start by defining a regional "climate index". The index should be a scalar metric which can be evaluated at every timestep. For example, in class we defined the Woods Hole sea surface temperature (SST) metric as the SST averaged along the coastline close to Woods Hole. For the assignment, choose a different location and/or a different variable$^1$ (e.g., sea level pressure in the North Pacific). You may also want to change how the index is computed (e.g., averaging over a larger/smaller area, or defining an index as the difference between two area averages).

```{admonition} Hint: choosing a variable$^1$
:class: hint

For this assignment, we recommend using a 2-dimensional variable for the index (e.g., 2m air temperature, sea level pressure, SST), as the data files for 3-dimensional variables (like temperature and salinity as a function of depth) are much larger.
```

```{admonition} To-do
In your submission, include a plot of your region (e.g., plotting the first timestep) and description of your index. Make sure your plots are labeled (e.g. label axes, labels, colorbars, etc.).
```

## 2) Compute statistics for the reanalysis (2 pts)
After defining a regional climate index, make a few diagnostic plots of the region and index. The goal is to get a sense for the climate in the region. E.g., some questions to think about may include:
- what is the mean state in your region and how big are typical fluctuations?
- how big are these fluctuations relative to the seasonal cycle?
- what is the timescale of these fluctuations?
- are fluctuations of your index correlated with larger-scale fluctuations?

To address these questions, some possible diagnostic plots include:
- spatial plots of mean, variance
- line/bar plot of index's seasonal cycle (e.g., showing mean and variance for each month)
- histogram of index anomalies (Does the distribution look normal?)
- power spectral density of the index
- spatial plot showing correlation between your index and data at each gridpoint 

```{admonition} To-do
In your submission, include a few (3-4) diagnostic plots of the climate in your region.
```

## 3) Compare statistics between model and reanalysis (3 pts)
### 3a) Compute statistics for CESM2 model
Your next task is to evaluate how well the CESM2 model simulates the climate in your region. To do this, start by computing the same statistics as above (e.g. mean, variance, power spectral density, etc.) but for the model instead of the reanalysis$^2$. You don't need to include anything from this part (3a) in your write-up.

```{warning}
Make sure you compute the statistics for each dataset over an overlapping time period (e.g., if the reanalysis spans 1979–present and the model spans 1950–2014, you would compute the statistics for each dataset over the period 1979–2014).
```

`````{admonition} Hint: relabeling coordinates$^2$
:class: hint

The spatial coordinates for renanalysis and model datasets may have different names (e.g., "lon" vs. "longitude") and orderings/conventions (e.g., latitude in ascending vs. descending order, or longitudes ranging from $0^{\circ}\to 360^{\circ}$ vs. $-180^{\circ} \to 180^{\circ}$). These differences may cause errors if you try to apply the same computation/plotting functions from Part 2 to the model output. 

One way around this is to rename/reorder the model output coordinates to match those of the reanalysis before trying to compute statistics. The following ```xarray``` functions may be useful for this:
```python
## rename data's coords from "lat"/"lon" to "latitude"/"longitude"
data = data.rename({"lat":"latitude", "lon":"longitude"})

## reverse direction of "latitude" coordinate
data = data.reindex({"latitude" : data["latitude"].values[::-1]})
`````

### 3b) Comparison plots
Next, compare the model's statistics to the reanalysis's statistics by making a few plots. One suggestion is to overlay the index-related statistics from both reanalysis and model onto the same plot (e.g., seasonal cycle, histogram of anomalies, power spectral density). Another is to plot the *difference* between the statistics of each dataset. 

Looking at the difference may be useful for spatial plots but can be challenging because the reanalysis and model data are often on different grids$^3$. If you don't want to deal with this regridding challenge, you could just plot the spatial fields side-by-side.

```{admonition} To-do
In your submission, include a few (3-4) comparison plots between the reanalysis and model datasets.
```

`````{admonition} Hint: regridding data$^3$
:class: hint

It's likely that the spatial coordinates for the reanalysis and model will differ (e.g., one may have a datapoint every $0.25^{\circ}$ while the other has a datapoint every $1^{\circ}$). If you'd like to do a gridpoint-by-gridpoint comparison (e.g., for a spatial plot) you may need to interpolate or "regrid" one of the datasets to match the other. Some possible tools for this include:
```python
## 1) interpolate reanalysis data onto model's grid using xarray
reanalysis_data = reanalysis_data.interp_like(model_data)

## 2) same, but using xesmf package
## (useful if one of the grids is not "regular")
import xesmf as xe
regridder = xe.Regridder(ds_in = reanalysis_data, ds_out=model_data)
reanalysis_data = regridder(reanalysis_data)
`````


## 4) Assess the model's performance (3 pts)
Finally, assess how well the model's statistics matches the reanalysis's statistics. Some questions to think about include:
- What's your overall impression of the model's performance?
- How well does it represent the statistics of your index?
- Would the model do a better job if you modified your index (e.g., increased the area for spatial averaging, or looked at annual rather than monthly averages?).

```{admonition} To-do
In your submission, write 3-4 sentences summarizing your takeaways.
```

## Hints

### Regridding data
The spatial coordinates for renanalysis and model datasets may have different names (e.g., "lon" vs. "longitude") and orderings/conventions (e.g., latitude in ascending vs. descending order, or longitudes ranging from $0^{\circ}\to 360^{\circ}$ vs. $-180^{\circ} \to 180^{\circ}$). These differences may cause errors if you try to apply the same computation/plotting functions from Part 2 to the model output. 

One way around this is to rename/reorder the model output coordinates to match those of the reanalysis before trying to compute statistics. The following ```xarray``` functions may be useful for this:
```python
## rename data's coords from "lat"/"lon" to "latitude"/"longitude"
data = data.rename({"lat":"latitude", "lon":"longitude"})

## reverse direction of "latitude" coordinate
data = data.reindex({"latitude" : data["latitude"].values[::-1]})
```