# CI2025_lab2
A specialized Genetic Algorithm implementation for solving the Traveling Salesman Problem (TSP), with optimized strategies for both symmetric and asymmetric distance matrices.
## Overview

Detects symmetric vs asymmetric distance matrices
Applies specialized strategies optimized for each problem type

## Symmetric Problems (e.g., Euclidean distances)
### Operators:

 #### Crossover: 
 Order Crossover (OX) - preserves relative ordering of cities
#### Mutation:

##### Inversion mutation:
 (80% probability) - reverses segments to maintain tour structure
##### Swap mutation:
 (20% probability) - occasional random swaps for diversity


##### Local Search: 
2-opt optimization applied to best solution at the end

#### Why these choices?

-OX preserves good subtours common in symmetric problems
-Inversion mutation respects the symmetric property of distances
-2-opt is highly effective for symmetric TSP, quickly finding local optima

## Asymmetric Problems (e.g., directed graphs, one-way streets)
### Operators:

#### Crossover: 
Partially Mapped Crossover (PMX) - preserves absolute positions
### Mutation (evenly distributed):

#### Swap mutation:
 (40%) - exchanges two cities
#### Scramble mutation:
 (30%) - shuffles a segment
#### Displacement mutation:
 (30%) - moves a segment to a new position


#### Local Search: 
None (2-opt can worsen asymmetric solutions)

### Why these choices?

-PMX better handles position-dependent costs in asymmetric matrices
-Diverse mutation operators provide more exploration
-Asymmetric problems require more aggressive search strategies
-2-opt is avoided as it assumes symmetric edge costs

## Algorithm Parameters
### Symmetric Strategy

-Tournament size: 60-100 (faster convergence)
-Population size: 500-800
-Mutation rate: 0.1 (adaptive)
-Stopping criterion: 50 generations without improvement

### Asymmetric Strategy

-Tournament size: 20-30 (more exploration)
-Population size: 600-1000 (larger for harder problems)
-Mutation rate: 0.15 (higher for diversity)
-Stopping criterion: 60 generations without improvement

## Initialization
### Both strategies use:

-10% greedy solutions: Nearest neighbor heuristic from different starting cities
-90% random solutions: Maintains genetic diversity

This hybrid initialization provides a good starting point while preserving exploration capability.