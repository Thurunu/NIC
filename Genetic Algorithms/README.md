# Genetic Algorithm for Optimization Problem

This project implements a Genetic Algorithm (GA) to solve an optimization problem where a set of values must satisfy specific constraints. The algorithm evolves solutions through selection, crossover, and mutation.

## Problem Definition
The objective of this optimization problem is to compute a solution for the equation:

```
F(x) = 3x1 + 2x2 + 4x3 + 2x4 + 5x5 = 100
```

Where `x1, x2, x3, x4, x5` are binary values representing genes in the chromosomes.

## Components of the Genetic Algorithm
The implementation includes the following key components:

1. **Population Initialization**
   - Randomly generates an initial population of solutions (chromosomes).

2. **Objective Function**
   - Calculates the fitness score of each chromosome based on the given equation.

3. **Selection**
   - Selects parents for the next generation based on their fitness scores.

4. **Crossover**
   - Combines genes from two parents to produce offspring.

5. **Mutation**
   - Introduces random changes to chromosomes to maintain genetic diversity.

6. **Termination**
   - The algorithm runs for a specified number of generations.

## Project Files
- **Main Code**: The entire genetic algorithm is implemented in the provided Jupyter Notebook file.

## Requirements
This project uses Python libraries for basic operations. Ensure the following dependencies are installed:

```bash
pip install numpy matplotlib
```

## How to Run the Project
1. **Install Python and Jupyter Notebook** (if not already installed):
   - Use Anaconda or install with pip:
     ```bash
     pip install notebook
     ```
2. **Run the Jupyter Notebook**:
   - Open the notebook:
     ```bash
     jupyter notebook GeneticAlgorithmPracticle_2.ipynb
     ```
3. **Execute the Code**:
   - Run all cells sequentially.
   - Observe the outputs, including the fitness scores, population changes, and final solutions.

## Results
The algorithm evolves a population of solutions over multiple generations to find the optimal chromosome that satisfies:
```
3x1 + 2x2 + 4x3 + 2x4 + 5x5 = 100
```
The output includes intermediate fitness scores, the evolving population, and the final solution.

## Example Output
```
Generation 0: Best Fitness = 5
Generation 1: Best Fitness = 3
...
Final Solution: [x1, x2, x3, x4, x5] with Fitness = 0
```

## Customization
You can customize the following parameters within the code:
- **Population Size**: Adjust the size of the initial population.
- **Number of Generations**: Control how many generations the algorithm runs.
- **Mutation Rate**: Set the probability of mutation for each chromosome.

## Author
This project was implemented as part of a practical exercise to demonstrate the Genetic Algorithm.
