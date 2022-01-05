from random import shuffle, uniform
from sys import maxsize


class GeneticAlgorithm:

    def __init__(self, waypoints: list, species=5, generation=5):
        self.waypoints = waypoints
        self.species = species
        self.generation = generation
        self.__population = []
        self.__fitness = [0.0] * species
        self.optimization = 0
        if species and generation:
            self.generate_population()
            self.calculate_fitness()
        else:
            print("No species or population")

    def generate_population(self):
        locations = len(self.waypoints)
        for _ in range(self.species):
            number_of_species = list(range(1, locations))
            shuffle(number_of_species)
            self.__population.append(number_of_species)
        return self.__population

    def calculate_fitness(self):
        total = maxsize
        best = None
        counter = 0
        for species in self.__population:
            weight = location = 0
            for points in species:
                weight += self.waypoints[location][points]
                location = points
            weight += self.waypoints[location][0]
            if total > weight:
                total = weight
                best = counter
            self.__fitness[counter] = 1 / (weight + 1)
            counter += 1
        self.normalization()
        return total, best

    def normalization(self):
        fitness_sum = sum(self.__fitness)
        i = 0
        for _ in self.__fitness:
            self.__fitness[i] = (self.__fitness[i] / fitness_sum)
            i += 1

    def next_generation(self):
        idx = 0
        selection = uniform(0, 1)
        while selection > 0:
            selection -= self.__fitness[idx]
            idx += 1
        idx -= 1
        return self.__population[idx]

    def get_fitness(self):
        return self.__fitness

    def get_population(self):
        return self.__population

    def solution(self):
        return self.optimization
