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

### 1. **Population Initialization**
The initial population is randomly generated with binary values for each gene. Each chromosome represents a candidate solution.

**Code Example**:
```python
population = [[random.randint(0, 1) for _ in range(5)] for _ in range(population_size)]
```
Here:
- `random.randint(0, 1)` generates binary values (0 or 1).
- The population is a list of chromosomes, where each chromosome has 5 genes.

### 2. **Objective Function**
The objective function calculates the fitness score of each chromosome based on how close the solution is to the target value (100).

**Code Example**:
```python
def objective_function(population):
    values = [3, 2, 4, 2, 5]
    fitness_score = []
    for chromosome in population:
        score = 0
        for x in range(len(values)):
            score += values[x] * chromosome[x]
        fitness_score.append(abs(score - 100))
    return fitness_score
```
Here:
- `values` represents the coefficients `[3, 2, 4, 2, 5]`.
- Each chromosome is evaluated by summing the product of the gene values and their respective coefficients.
- The fitness score is calculated as the absolute difference from the target value (100).

### 3. **Selection**
Selection chooses the best-fit individuals (chromosomes) to act as parents for the next generation. This implementation uses cumulative probability-based selection.

**Code Example**:
```python
def selection(population, fitness_scores):
    total_fitness = sum(fitness_scores)
    probabilities = [1 - (score / total_fitness) for score in fitness_scores]
    selected_parents = []
    for _ in range(len(population)):
        r = random.random()
        cumulative = 0
        for i, prob in enumerate(probabilities):
            cumulative += prob
            if r <= cumulative:
                selected_parents.append(population[i])
                break
    return selected_parents
```
Here:
- Fitness scores are converted into probabilities.
- Parents are selected using a cumulative probability approach.
- The better the fitness score, the higher the chance of being selected.

### 4. **Crossover**
Crossover combines genes from two parents to create offspring. This implementation uses a **single-point crossover** strategy.

**Code Example**:
```python
def crossover(parent1, parent2):
    point = random.randint(1, len(parent1) - 1)
    child1 = parent1[:point] + parent2[point:]
    child2 = parent2[:point] + parent1[point:]
    return child1, child2
```
Here:
- A random point is selected in the chromosome.
- The genes before the point are taken from one parent, and the genes after the point are taken from the other parent.
- Two children are produced.

### 5. **Mutation**
Mutation introduces randomness by altering genes in a chromosome, helping to maintain diversity in the population.

**Code Example**:
```python
def mutation(population, mutation_rate):
    for chromosome in population:
        for i in range(len(chromosome)):
            if random.random() < mutation_rate:
                chromosome[i] = 1 - chromosome[i]  # Flip 0 to 1 or 1 to 0
    return population
```
Here:
- `mutation_rate` controls the probability of a gene being mutated.
- A gene is flipped (0 to 1 or 1 to 0) based on this probability.

### 6. **Termination**
The algorithm runs for a fixed number of generations, and the best solution is selected based on the fitness score.

**Code Example**:
```python
for generation in range(num_generations):
    fitness_scores = objective_function(population)
    population = selection(population, fitness_scores)
    next_generation = []
    for i in range(0, len(population), 2):
        child1, child2 = crossover(population[i], population[i+1])
        next_generation.extend([child1, child2])
    population = mutation(next_generation, mutation_rate)
```
Here:
- The algorithm iterates through a fixed number of generations.
- The population evolves through selection, crossover, and mutation.
- The best solution is obtained based on the fitness scores.

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
