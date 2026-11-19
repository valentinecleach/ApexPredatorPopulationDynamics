# Estimating and forecasting spatial population dynamics of apex predators using transnational genetic monitoring


## Overview
This academic project builds upon the article by  [R. Bischof et al. (2020), *Estimating and forecasting spatial population dynamics of apex predators using transnational genetic monitoring*](https://doi.org/10.1073/pnas.201138311). The project had two main goals:
- **popularisation** of the mathematics involved in the paper,  
- **test the limits** of the model using simulations that break different key hypotheses.

This code of the main model stems from the [git repository](https://github.com/richbi/WildThings) mentioned in the original article.

The model presented in the article follows populations of 3 species of apex predators (wolverines, wolves and bears) across space (Norway and Sweden) and time (from 2012 to 2019). It uses datasets of detection/non-detection at a time and location by collecting samples of DNA and indentifying individuals from one another. 

## Key Contributions and Techniques

### The OPSCR Model
The model used was an Open Population Spatial Capture Recapture (OPSCR) model. The model uses:
* a discrete Markov process to model the size of the populations
* an initial spatial distribution to evaluate a likely location for each individual
* a multivariate normal source point inhomogeneous binomial point process to determine how an individual moves across the territory.
* A half-normal detection model to represent difficulties in detecting certain individuals or certain locations
* Bayesian inference to estimate the model (nimble)

### Key Contributions
We investigated the assumption that individual activity centres follow a homogeneous Poisson point process. We implemented simulations following two different processes where this is not the case:
* **A Strauss Process**: Models spatial inhibition, meaning individuals tend to avoid being located close to one another. This could represent solitary predators like wolverine populations.
* **A Neyman-Scott Process**: Models spatial clustering, meaning individuals tend to occur in groups or clusters. This could reprensent populations that live in packs.
We then fitted the model to these simulated datasets and used relative bias and the coefficient of variation to assess the impact of these alternative spatial processes.

## Technology Stack & Requirements
* **Language**: R 4.5.0
* **Core Libraries:** [dplyr](https://dplyr.tidyverse.org/), [ggplot2](https://ggplot2.tidyverse.org/), [nimble](https://r-nimble.org/), [nimbleSCR](https://github.com/nimble-dev/nimbleSCR), [sf](https://r-spatial.github.io/sf/), [spatstat](https://spatstat.org/)

## Collaborators
* Valentine CLEACH - valentine.cleach@gmail.com
* Fanny MOREAU - fanny.moreau32@gmail.com
  
This is a completed academic project. However, feedback on the methodology or analysis is welcome.

## References
The project builds upon the following scientific literature, technical documentation and academic courses:

1. **Bischof, R. et al. (2020).** *Estimating and forecasting spatial population dynamics of apex predators using transnational genetic monitoring.* Proceedings of the National Academy of Sciences.
   [https://doi.org/10.1073/pnas.2011383117](https://doi.org/10.1073/pnas.2011383117)
3. **Floch, J.-M., Marcon, E. & Puech, F.** *Les configurations de points.* INSEE.
   [Document](https://www.insee.fr/fr/statistiques/fichier/3635442/imet131-h-chapitre-4.pdf)
4. **Reich, H., Vasquez, J. & Osterhout, M. (2021).** *Spatial Capture-Recapture.*
   [Course materials](https://kevintshoemaker.github.io/NRES-746/SCR.html)
8. **Bischof, R., Dupont, P., Milleret, C., Chipperfield, J. & Royle, J. A. (2019).** *Consequences of ignoring group association in spatial capture–recapture analysis.* Wildlife Biology.
   [https://doi.org/10.2981/wlb.00649](https://doi.org/10.2981/wlb.00649)
