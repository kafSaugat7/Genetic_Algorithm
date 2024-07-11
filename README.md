# Introduction: 
A genetic algorithm is a problem-solving technique inspired by the principles of natural evolution. It works by simulating the process of natural selection and genetic inheritance to find optimal or near-optimal solutions to complex problems. The algorithm starts with a population of potential solutions, each represented as a "chromosome" encoding specific traits. 
This documentation explains how a genetic algorithm is used to find solutions to the equation 2x^2 + 5x - 3 = 0. The process mimics biological evolution to search for optimal solutions.

# Problem Definition: 
1.	Equation to solve: 2x^2 + 5x - 3 = 0
2.	Goal: Find values of x that make this equation true (or very close to true)

# Installation (Jupyter)
To run this project locally,follow these steps:

1. **Clone the repository:**

   ```sh
   git clone

2. **Create a virtual environment (optional but recommended):**
 Creating a virtual environment is recommended to keep project dependencies isolated.
'''sh
python -m

3. **Install Jupyter Notebook and dependencies:**
 Install Jupyter Notebook and other dependencies using pip.

4.**Start Jupyter Notebook:**
Launch Jupyter Notebook to run the genetic algorithm notebook.

5.**Open the notebook:**
Navigate to the genetic_algorithm.ipynb file in your Jupyter Notebook interface and open it to execute the genetic algorithm code.

6.**Shutdown Jupyter Notebook:**
Once finished, you can shut down Jupyter Notebook by pressing Ctrl + C in the terminal where it's running and confirming the shutdown.

7.**Deactivate virtual environment (if used):**



# **Genetic Algorithm Documentation**


## 	**Fitness Function**

The fitness function evaluates how well a particular solution (chromosome) solves the problem. In this example, the fitness function is defined as:
f(x)=∣2x2+5x−3∣f(x) = |2x^2 + 5x - 3|f(x)=∣2x2+5x−3∣
The goal is to minimize this function.
```python
# Function to calculate fitness (lower is better)
def calculate_fitness(x):
	return abs(2 * x**2 + 5 * x - 3
```

## **   Binary Encoding**

Binary encoding is used to represent potential solutions (chromosomes) as binary strings. Each chromosome consists of 11 bits:
* The first bit represents the sign (0 for positive, 1 for negative).
* The next 4 bits represent the integer part of the number.
* The last 6 bits represent the fractional part (residual part) of the number.

```python
# Function to create a random chromosome
def create_chromosome():
    return [random.choice([0, 1]) for _ in range(11)]

# Function to decode a chromosome into a number
def decode_chromosome(chromosome):
    sign = -1 if chromosome[0] == 1 else 1
    integer_part = int(''.join(map(str, chromosome[1:5])), 2)
    residual_part = int(''.join(map(str, chromosome[5:])), 2) / 64
    return sign * (integer_part + residual_part)
```

## ** Creating a Random Chromosome**

```python
# Function to create a random chromosome
def create_chromosome():
	return [random.choice([0, 1]) for _ in range(11)]
```

## **   Decoding a Chromosome**

The binary string is decoded back to a floating-point number.

```python
# Function to decode a chromosome into a number
def decode_chromosome(chromosome):
	sign = -1 if chromosome[0] == 1 else 1
	integer_part = int(''.join(map(str, chromosome[1:5])), 2)
	residual_part = int(''.join(map(str, chromosome[5:])), 2) / 64
	return sign * (integer_part + residual_part)
```

## **	Uniform Crossover**
Uniform crossover is a genetic operator used to combine the genetic information of two parents to generate a new offspring. Each gene (bit) of the offspring is chosen randomly from either parent.

```python
# Function to perform crossover
def crossover(parent1, parent2):
	child = []
	for i in range(len(parent1)):
    	if random.random() < 0.5:
        	child.append(parent1[i])
    	else:
        	child.append(parent2[i])
	return child
```

## **	Mutation**
Mutation is a genetic operator used to maintain genetic diversity. It randomly flips one bit in the chromosome.
```python
# Function to perform mutation
def mutate(chromosome):
    index = random.randint(0, len(chromosome) - 1)
    chromosome[index] = 1 - chromosome[index]  # Flip the bit
    return chromosome
```























   

