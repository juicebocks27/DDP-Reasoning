# Circular Seating Arrangement

This project explores circular seating arrangements for representatives, providing functions to evaluate, validate, and query seating configurations based on specific conditions. It also includes visualization tools for plotting arrangements.

---

## Repository Structure

This repository contains two primary files:

1. **`Round_Table_v3.ipynb`**
   - Contains all the helper functions that act as the text corpus for the LLM (Large Language Model) functionality.
   - These functions solve circular seating arrangement problems by exploring various permutations and applying logical conditions.

2. **`Round_table_llm_v2.ipynb`**
   - Builds upon the helper functions from `Round_Table_v3` and integrates them with an LLM.
   - The LLM uses these functions as context to generate and execute Python code combinations to solve complex reasoning problems related to circular arrangements.

These files provide a framework for solving advanced logical reasoning challenges by combining helper functions with LLM-powered execution.

---

## Features and Functions

### **Core Functions**
1. **`normalize(arrangement)`**
   - **Definition**: Normalizes an arrangement to its lexicographically smallest rotation to handle circular symmetry.
   - **Logic**: Generates all rotations of the arrangement and selects the smallest one lexicographically.

2. **`seating_positions_from_arrangement(arrangement)`**
   - **Definition**: Converts an arrangement into a dictionary mapping chair positions (1 to N) to representatives.
   - **Logic**: Enumerates the arrangement and creates a dictionary with chair numbers as keys.

---

### **Query Functions**
1. **`who_sits_on_left(seating_positions, person)`**
   - **Definition**: Determines who sits to the left of a specific person in a seating arrangement.
   - **Logic**: Finds the person's position and calculates the left position cyclically.

2. **`who_sits_on_right(seating_positions, person)`**
   - **Definition**: Determines who sits to the right of a specific person in a seating arrangement.
   - **Logic**: Finds the person's position and calculates the right position cyclically.

3. **`who_sits_between(seating_positions, person1, person2)`**
   - **Definition**: Finds who sits between two specific people in a circular seating arrangement.
   - **Logic**: Calculates clockwise positions and identifies the person in between.

4. **`query_neighbors(seating_position, person)`**
   - **Definition**: Prints the left and right neighbors of a person in a given arrangement.
   - **Logic**: Uses `who_sits_on_left` and `who_sits_on_right` to determine neighbors.

5. **`query_between(seating_position, person1, person2)`**
   - **Definition**: Finds and prints who sits between two specific people.
   - **Logic**: Uses `who_sits_between` to determine the result.

---

### **Validation Functions**
1. **`is_valid_arrangement(arrangement, valid_set)`**
   - **Definition**: Checks if a given arrangement is valid by normalizing and comparing it with valid arrangements.
   - **Logic**: Uses the `normalize()` function and the set of valid arrangements.

2. **`find_valid_arrangements(arrangements, conditions)`**
   - **Definition**: Finds all unique, valid seating arrangements based on specified conditions.
   - **Logic**: Checks all permutations of arrangements against conditions and returns unique normalized configurations.

---

### **Visualization**
1. **`plot_circular_seating(arrangement)`**
   - **Definition**: Plots a circular representation of a seating arrangement.
   - **Logic**: Uses `networkx` to create a directed graph and displays the arrangement with a circular layout.

---

## Usage Example

```python
# Define representatives
representatives = ['K', 'L', 'M', 'N', 'O', 'P']

# Define conditions for seating
condition_1 = lambda arrangement: sits_next_to(arrangement, 'P', 'N')
condition_2 = lambda arrangement: sits_next_to_any(arrangement, 'L', ['M', 'N'])
condition_3 = lambda arrangement: does_not_sit_next_to(arrangement, 'K', 'M')
condition_4 = lambda arrangement: sits_next_to_and_not_next_to(arrangement, 'O', 'P', 'M')
conditions = [condition_1, condition_2, condition_3, condition_4]

# Generate valid arrangements
from itertools import permutations
valid_arrangements = find_valid_arrangements(permutations(representatives), conditions)

# Visualize a valid arrangement
if valid_arrangements:
    arrangement = list(valid_arrangements)[0]
    plot_circular_seating(arrangement)
