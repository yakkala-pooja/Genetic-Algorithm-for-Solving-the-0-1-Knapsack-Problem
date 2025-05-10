
# Genetic Algorithm for Solving the 0-1 Knapsack Problem

## Overview

This project implements a **Genetic Algorithm (GA)** to solve the classical **0-1 Knapsack Problem** — an NP-complete combinatorial optimization problem. The algorithm evolves a population of candidate solutions through selection, crossover, and mutation operations to find an optimal or near-optimal subset of items that maximizes total value without exceeding the knapsack's capacity.

This approach is particularly suitable for large or complex datasets where exhaustive search is computationally infeasible.

---

## Features

- Binary representation of candidate solutions (chromosomes)
- Configurable knapsack settings via input config file
- **Two selection strategies**:
  - Roulette Wheel Selection
  - Tournament Selection
- **Genetic operators**:
  - Single-point crossover
  - Bit-flip mutation with customizable mutation rate
- Fitness evaluation with support for constraint handling
- Logging and plotting of generation-wise performance
- Support for experimentation with multiple population sizes and configurations
- Optional custom fitness functions and stop criteria (extra features)
- Comparative evaluation against non-GA baseline algorithms (e.g., dynamic programming)

---

## Project Structure

```
knapsack-ga/
├── config/
│   ├── config.txt
│   ├── config_1.txt
│   └── config_2.txt
├── notebook/
│   └── GA.py
├── baseline/
│   └── Baseline.py
├── README.md
└── requirements.txt
```

---

## How It Works

### 1. Problem Setup
A plain-text configuration file specifies:
- Population size
- Number of generations
- Knapsack capacity
- List of items `(weight, value)`

### 2. Initialization
A population of individuals (chromosomes) is randomly initialized. Each individual is a binary string of length `n`, where `1` denotes inclusion of the item.

### 3. Fitness Evaluation
Each chromosome's fitness is the total value of the selected items, **only if the total weight does not exceed the capacity**. Otherwise, the fitness is zero.

### 4. Selection Strategies
- **Roulette Wheel Selection**: Individuals are probabilistically chosen based on fitness proportion.
- **Tournament Selection**: A set of individuals competes, and the fittest is chosen.

### 5. Crossover and Mutation
- Single-point crossover randomly selects a point and exchanges segments between two parents.
- Bit-flip mutation randomly flips bits in the chromosome based on a mutation rate.

### 6. Evolution Loop
The population evolves over a defined number of generations. At each generation:
- Selection → Crossover → Mutation → Replacement

---

## Example Results

Fitness progression plots show the evolution of:
- Average fitness across generations
- Best fitness individual per generation
- Number of items in best solution

Tabular summaries report:
- Mean and standard deviation of fitness over multiple trials
- Final weights and item counts of top solutions

---

## Configuration

Sample `config.txt` file:

```
50           # population size
10           # number of items
100          # number of generations
15           # knapsack capacity
2 3          # (weight, value) of item 1
1 2
...
```

---

## Experiments

You can run:
- GA with only selection (no crossover or mutation) for baseline insight
- GA with full evolutionary loop
- Comparisons across different selection methods and mutation rates
- Population size impact analysis (e.g., 10, 20, ..., 200)
- Alternative algorithms like Dynamic Programming

---

## Run Instructions

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Run GA

```bash
python notebook/GA.py --config config/config1.txt --selection roulette --mutation_rate 0.1
```

### Run Baseline

```bash
python baseline/Baseline.py
```

---

## Learnings and Insights

This project provides a flexible framework to study the impact of genetic algorithm parameters on the 0-1 Knapsack Problem. It also offers a direct comparison to traditional approaches like dynamic programming, showcasing strengths of evolutionary methods in scenarios with large or complex search spaces.

---

## References

- Goldberg, D. E. (1989). *Genetic Algorithms in Search, Optimization and Machine Learning*
- Mitchell, M. (1998). *An Introduction to Genetic Algorithms*
- [Wikipedia - Knapsack Problem](https://en.wikipedia.org/wiki/Knapsack_problem)

---
