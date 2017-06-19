# Metaheuristics-library-placeholder

## Current Features:
* Genetic Algorithm
* Evolutionary Algorithm
* Simulated Annealing
* Particle Swarm Optimization
* Tabu Search
* Harmony Search
* Stochastic Hill Climb

<hr>

## Usage:
* ```pip install``` 
* Import the relevant algorithm
* Create a class that inherits from that algorithm, and that implements the necessary abstract methods
* Call its ```.run()``` method

<hr>

## Example:

```python
from random import choice, randint, random
from string import lowercase
from library.EvolutionaryAlgorithm import EvolutionaryAlgorithm


class Algorithm(EvolutionaryAlgorithm):
    """
    Tries to get a randomly-generated string to match string "clout"
    """
    def _initial_population(self):
        return list(''.join([choice(lowercase) for _ in range(5)]) for _ in range(50))

    def _fitness(self, member):
        return float(sum(member[i] == "clout"[i] for i in range(5)))

    def _crossover(self, parent1, parent2):
        partition = randint(0, len(self.population[0]) - 1)
        return parent1[0:partition] + parent2[partition:]

    def _mutate(self, member):
        if self.mutation_rate >= random():
            member = list(member)
            member[randint(0,4)] = choice(lowercase)
            member = ''.join(member)
        return member


def test_algorithm():
    algorithm = Algorithm(.5, .7, 500, max_fitness=None)
    algorithm.run()

```

<hr>

## Building and Testing

To run tests, look in the ```tests``` folder. 

I use [pytest](https://docs.pytest.org/en/latest/); it should automatically find the test files. 

<hr>

## Contributing

Feel free to send a pull request if you want to add any features or if you find a bug.

Check the issues tab for some potential things to do.

