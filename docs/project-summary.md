# Project Summary

This project studies Madrid air quality using the METRAQ dataset, which contains hourly observations from 2001 to 2024.

The aim was not just to plot pollutant levels. We wanted to build a reproducible pipeline that could clean the data, compare imputation strategies, study temporal and spatial patterns, and test whether weather, traffic and calendar variables could explain monthly NO2 levels.

## Main workstreams

1. **Data inspection and cleaning**
   - Reviewed the structure of the METRAQ dataset.
   - Kept the original interpolation flag instead of discarding it.
   - Treated physically impossible values as missing while keeping heavy-tailed pollution spikes.

2. **Imputation comparison**
   - Compared METRAQ spatial interpolation, temporal linear interpolation, KNN and regression-based imputation.
   - Used KS distance to compare imputed values against the observed distribution.
   - Built a best-of-breed dataset by selecting the most suitable method variable by variable.

3. **Temporal and spatial analysis**
   - Aggregated pollutant patterns by month, hour and season.
   - Compared distance-based sensor networks with k-nearest-neighbour networks.
   - Built correlation networks to identify sensors that behave similarly even when they are not geographically close.

4. **Parallel computation**
   - Benchmarked sequential vs. multiprocessing correlation calculations.
   - Found useful speedups up to a few workers, with diminishing returns once process overhead became dominant.

5. **NO2 forecasting**
   - Tested whether weather, traffic and calendar variables could predict monthly NO2.
   - Compared a Random Forest model against a linear baseline on a held-out 2023 test set.

## Key takeaways

- NO2 declined substantially over the 2001-2024 period, while ozone increased gradually.
- Traffic-related pollutants show strong daily and yearly cycles.
- Wind speed is negatively associated with NO2, while NO, NOX and traffic intensity move positively with it.
- A Random Forest model performed much better than the linear baseline for the NO2 forecasting task.
- Parallelization helped, but the workload was not large enough per task for speedup to scale indefinitely.

## Authors

Matteo Bruni, Federico Romano Gargarella, Matteo Rapisarda.
