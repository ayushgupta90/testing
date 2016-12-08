# NSGA-II with CDOM and BDOM + Cuboid distance secondary sorters

## Abstract
This experiment explores the difference between NSGA-II with different secondary sort operators. With this setup we tried to explore the diffrence between using binary domination with cuboid distances and continuous domination as two different types of selection operators. It turns out that both seem about the same in terms of impact on hypervolume reguardless of the number of objectives used.

## Introduction
### Genetic Algorithm
Genetic Algorithms are a type of optimization technique that keep a collection as solutions known as a population. During each iteration of this algorithm, the populations decisions are bred with eachother and mutated. Then the newly created population is compared to itself and the best out of the new population is saved.

### NSGA-II
![alt tag](https://github.com/txt/ase16/blob/master/img/nsgaii.png?raw=true)
Similar to a standard genetic algorithm with a different metric for selection. NSGA-II uses a quick frontier based non-dominated sort to begin with. After the frontiers are sorted, a secondary sort is to the front that contains more samples than is neccicary for the population. The number of simples needed to maintain the population is kept while the remainder are dropped. The secondary sort mechanic is where the two implementions of the algorithm differ.

#### Bdom + Cuboid
Cuboid distances is basically the sum of the verticle spaces between the closest candidates to a point. 
![alt tag](https://github.com/txt/ase16/blob/master/img/cuboid.png?raw=true)

#### Cdom

### Models
#### DTLZ1
#### DTLZ3
#### DTLZ5
#### DTLZ7
![alt tag](http://people.ee.ethz.ch/~sop/download/supplementary/testproblems/dtlz7/images/dtlz7_Formulation.png)
DTLZ7 is a model created in order to test the potential for optimizers to find and maintain several distinct disjointed pareto-optimal solutions. As you can see, when using two objectives, x1 and x2, the pareto-optimal regions are spread out quite a bit. With DTLZ7 it is possible to implement the model using any number of objectives and any number of decisions.

### Result Analysis
#### Hypervolume
Hypervolume is area that the pareto frontier contains. Essentially the size of the area that can contain non-pareto solutions. The better the hypervolume, the greater the area explored and the better the pareto solutions.

#### Scott-Knott
The Scott-Knot test is used for clustering results into similar categories. Scott-Knot recursively bi-clusters the output from each of the optimizers into ranks. At each level of ranks, another split is created where the expected values are the most different. Before continuing, Boostrap (random sampling) and A12 are called to check and see if the splits are significantly different.

This is used in order to determine if there is a significant difference between the resulting hypervolumes for each algorithm.

## Experimental Setup
NSGA-II is applied to DTLZ1, DTLZ3, DTLZ5, DTLZ7 with a veriety of configurations. Each model is testd with 10, 20 and 40 decisions with 2, 4, 6, and 8 objectives. Each permutation of models, the number of decisions and number of objectives are also executed with both Bdom + Cuboid and Cdom as secondary sorting operations. 20 Runs are executed for each permutation of model. After the execution of models, the hypervolume is measured for each optimized solution.

## Results
Each of the results below show an analysis of the hypervolumes generated by NSGA-II given the paramaters under the 'name' column. For example 'dtlz1 8 10 bdom' means NSGA-II optimized the model dtlz1 with 8 objectives and 10 decisions. Each of the hypervolumes are normalized from 0-1. The higher the number, the better the result.

```
rank ,         name ,    med   ,  iqr 
----------------------------------------------------
   1 , dtlz1 8 10 bdom ,      97  ,     0 (               |             *), 0.97,  0.97,  0.97,  0.97,  0.97
   1 , dtlz1 8 10 cdom ,      97  ,     0 (               |             *), 0.97,  0.97,  0.97,  0.97,  0.97
   1 , dtlz1 8 20 bdom ,      97  ,     0 (               |             *), 0.97,  0.97,  0.97,  0.97,  0.97
   1 , dtlz1 8 20 cdom ,      97  ,     0 (               |             *), 0.97,  0.97,  0.97,  0.97,  0.97
   1 , dtlz1 8 40 bdom ,      97  ,     0 (               |             *), 0.97,  0.97,  0.97,  0.97,  0.97
   1 , dtlz1 8 40 cdom ,      97  ,     0 (---------------|-------------*), 0.00,  0.97,  0.97,  0.97,  0.97
   1 , dtlz1 6 10 bdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz1 6 10 cdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz1 6 20 bdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz1 6 20 cdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz1 6 40 bdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz1 6 40 cdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz1 4 10 bdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz1 4 10 cdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz1 4 20 bdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz1 4 20 cdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz1 4 40 bdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz1 4 40 cdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz1 2 10 bdom ,      99  ,     0 (               |             *), 0.99,  0.99,  0.99,  0.99,  0.99
   1 , dtlz1 2 10 cdom ,      99  ,     0 (               |             *), 0.99,  0.99,  0.99,  0.99,  0.99
   1 , dtlz1 2 20 bdom ,      99  ,     0 (               |             *), 0.99,  0.99,  0.99,  0.99,  0.99
   1 , dtlz1 2 20 cdom ,      99  ,     0 (               |             *), 0.99,  0.99,  0.99,  0.99,  0.99
   1 , dtlz1 2 40 bdom ,      99  ,     0 (               |             *), 0.99,  0.99,  0.99,  0.99,  0.99
   1 , dtlz1 2 40 cdom ,      99  ,     0 (               |             *), 0.99,  0.99,  0.99,  0.99,  0.99
```
Results for DTLZ1 are not pariticularly meaningful. Every algorithm ended up getting a near perfect hypervolume. No decerniable difference between cdom and bdom.

```
rank ,         name ,    med   ,  iqr 
----------------------------------------------------
   1 , dtlz3 8 10 bdom ,      97  ,     0 (---------------|-------------*), 0.00,  0.97,  0.97,  0.97,  0.97
   1 , dtlz3 8 10 cdom ,      97  ,     0 (               |             *), 0.97,  0.97,  0.97,  0.97,  0.97
   1 , dtlz3 8 20 bdom ,      97  ,     0 (               |             *), 0.97,  0.97,  0.97,  0.97,  0.97
   1 , dtlz3 8 20 cdom ,      97  ,     0 (               |             *), 0.97,  0.97,  0.97,  0.97,  0.97
   1 , dtlz3 8 40 bdom ,      97  ,     0 (               |             *), 0.97,  0.97,  0.97,  0.97,  0.97
   1 , dtlz3 8 40 cdom ,      97  ,     0 (               |             *), 0.97,  0.97,  0.97,  0.97,  0.97
   1 , dtlz3 6 10 bdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz3 6 10 cdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz3 6 20 bdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz3 6 20 cdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz3 6 40 bdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz3 6 40 cdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz3 4 10 bdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz3 4 10 cdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz3 4 20 bdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz3 4 20 cdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz3 4 40 bdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz3 4 40 cdom ,      98  ,     0 (               |             *), 0.98,  0.98,  0.98,  0.98,  0.98
   1 , dtlz3 2 10 bdom ,      99  ,     0 (               |             *), 0.99,  0.99,  0.99,  0.99,  0.99
   1 , dtlz3 2 10 cdom ,      99  ,     0 (               |             *), 0.99,  0.99,  0.99,  0.99,  0.99
   1 , dtlz3 2 20 bdom ,      99  ,     0 (               |             *), 0.99,  0.99,  0.99,  0.99,  0.99
   1 , dtlz3 2 20 cdom ,      99  ,     0 (               |             *), 0.99,  0.99,  0.99,  0.99,  0.99
   1 , dtlz3 2 40 bdom ,      99  ,     0 (               |             *), 0.99,  0.99,  0.99,  0.99,  0.99
   1 , dtlz3 2 40 cdom ,      99  ,     0 (               |             *), 0.99,  0.99,  0.99,  0.99,  0.99
```

Results to dtlz3 matched those of dtlz1.

```
rank ,         name ,    med   ,  iqr 
----------------------------------------------------
   1 , dtlz5 8 10 bdom ,      64  ,     1 (-*             |              ), 0.63,  0.63,  0.64,  0.65,  0.66
   1 , dtlz5 8 10 cdom ,      64  ,     2 ( *             |              ), 0.62,  0.63,  0.64,  0.64,  0.66
   2 , dtlz5 8 20 cdom ,      72  ,     4 (   - *--       |              ), 0.70,  0.71,  0.73,  0.76,  0.80
   2 , dtlz5 8 20 bdom ,      73  ,     4 (      *        |              ), 0.70,  0.71,  0.74,  0.75,  0.77
   3 , dtlz5 6 10 bdom ,      75  ,     2 (     -*        |              ), 0.74,  0.75,  0.75,  0.78,  0.78
   3 , dtlz5 6 10 cdom ,      77  ,     2 (      -*       |              ), 0.76,  0.77,  0.78,  0.79,  0.80
   4 , dtlz5 6 20 cdom ,      87  ,     5 (          - *- |              ), 0.84,  0.86,  0.89,  0.90,  0.92
   4 , dtlz5 6 20 bdom ,      89  ,     5 (          -- * |              ), 0.83,  0.89,  0.90,  0.92,  0.94
   5 , dtlz5 8 40 bdom ,      92  ,     3 (             *-|              ), 0.88,  0.89,  0.92,  0.93,  0.98
   5 , dtlz5 8 40 cdom ,      91  ,     5 (           -  *|-             ), 0.87,  0.90,  0.93,  0.94,  1.01
   5 , dtlz5 4 10 cdom ,      92  ,     2 (            - *|              ), 0.89,  0.91,  0.92,  0.94,  0.95
   5 , dtlz5 2 10 cdom ,      92  ,     0 (             -*|              ), 0.91,  0.92,  0.92,  0.93,  0.93
   5 , dtlz5 2 40 bdom ,      92  ,     2 (            - *|              ), 0.89,  0.91,  0.93,  0.93,  0.97
   5 , dtlz5 2 10 bdom ,      93  ,     1 (             -*|              ), 0.92,  0.92,  0.93,  0.93,  0.94
   5 , dtlz5 4 10 bdom ,      93  ,     1 (             -*|              ), 0.90,  0.92,  0.93,  0.94,  0.95
   5 , dtlz5 2 40 cdom ,      93  ,     4 (             -*|              ), 0.90,  0.92,  0.94,  0.95,  0.98
   5 , dtlz5 2 20 cdom ,      94  ,     2 (             -*|              ), 0.92,  0.93,  0.94,  0.94,  0.96
   5 , dtlz5 2 20 bdom ,      94  ,     1 (             - *              ), 0.92,  0.93,  0.94,  0.94,  0.96
   6 , dtlz5 4 20 bdom ,      99  ,     3 (               |-*            ), 0.97,  0.99,  1.01,  1.05,  1.07
   6 , dtlz5 4 20 cdom ,     101  ,     5 (               |- *-          ), 0.97,  0.99,  1.02,  1.04,  1.07
   6 , dtlz5 6 40 bdom ,     103  ,     9 (               |-- * ----     ), 0.95,  1.02,  1.04,  1.08,  1.18
   6 , dtlz5 6 40 cdom ,     104  ,    16 (           ----|--  *-------  ), 0.86,  1.02,  1.07,  1.08,  1.23
   7 , dtlz5 4 40 cdom ,     111  ,     2 (               |     -*--     ), 1.10,  1.11,  1.11,  1.13,  1.17
   7 , dtlz5 4 40 bdom ,     115  ,     1 (               |      --*---- ), 1.11,  1.15,  1.16,  1.17,  1.27
```

## Threats to Validity

## Future Work

## Refrences
