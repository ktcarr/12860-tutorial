# Background

## What is climate variability?
- First, what is climate? One definition: long-term statistics of the ocean/atmosphere/ice/land/etc
- Climate *variability*: "slow" changes in some property of ocean/atmosphere, which may appear to "oscillate"
- What is slow? Good question! One definition: longer than "weather" timescales (~2 weeks)
- Often think climate variability as a set of distinct "modes" (e.g., El Niño / La Niña, Madden-Julian Oscillation)
- These modes have different feedbacks/mechanisms which lead to different spatial patterns and timescales
- Almost like "emergent" properties - e.g., depend on continental configuration

## Observations, models, and reanalysis
- What's the difference? What do we use these tools for?

### Observations
- Gold standard: everything is based on these! E.g., use them to guide model development.
- Challenge: they're sparse!

### Models 
- (Mostly) physically-consistent evolution of climate system (solving differential equations).
- Easier to compute robust statistics (just run the model a bunch of times!) and study "modes" with long timescales
- Makes it possible to estimate future changes to climate (e.g., effect of greenhouse gas emissions)
- Challenge: for computational reasons, have to make approximations; these approximations lead to biases/errors.

### Reanalysis
- Uses a model to "fill the gaps" in observations
- Idea: atmosphere is chaotic, and simulations with slightly different initial conditions will diverge quickly (weather timescales).
- Therefore, we use the observations to "pull" the model back every few hours, so that it doesn't diverge.
- Have to make compromises: won't exactly match observations and won't conserve properties that should be conserved (unlike models)

## CMIP6 server
- Use GUI to browser output
- Using ```ncdump```

## Other places to find data
- Accessing ERA5 Google/ARCO from the cloud (this is the future !?)
- IMERG/TRMM?

## Plan
- **Today (in class)**: compute regional climate statistics in a *reanalysis* product
- **Assignment 1**: evaluate the same statistics in a climate *model*
- Next time: "modes" of climate variability!
