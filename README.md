# Nash Budget Decomposition

## Overview
This Python script implements an optimization approach to allocate a total budget across various issues based on the preferences of a group of citizens. It aims to achieve a fair and efficient distribution, ensuring that each citizen's preferences are taken into account as much as possible. The core of this method is based on principles from game theory, specifically utilizing a form of utility maximization to simulate a Nash bargaining solution. The objective is to find a budget decomposition that maximizes the overall satisfaction among the citizens, subject to the constraints of the total budget and the citizens' preferences.

## Requirements
- Python 3.6 or higher
- Numpy: For numerical operations.
- CVXPY: For solving the convex optimization problem.

To install the necessary Python packages, run:
```sh
pip install numpy cvxpy
```

## Usage
First, ensure you have the required packages installed in your Python environment. Then, you can include the function `find_decomposition_nash` in your Python script or notebook.

### Function Signature
```python
def find_decomposition_nash(budget, preferences):
    """
    Attempts to find a Nash budget decomposition based on citizens' preferences.

    Parameters:
    - budget (list of float): The total budget available for each issue.
    - preferences (list of sets): Each set contains the indices of issues a citizen supports.

    Returns:
    - str: A readable string describing the allocation if a feasible breakdown is found; otherwise, indicates no feasible breakdown.
    """
```

### Example
```python
budget = [0, 300]  # Budget for each issue
preferences = [{0}, {1}, {1}]  # Preferences of each citizen

# Find decomposition using the Nash approach
result = find_decomposition_nash(budget, preferences)
print(result)
```

## How It Works
The script converts the citizens' preferences into a matrix form, setting up an optimization problem where the objective is to maximize the sum of utilities derived from budget allocations to preferred issues. The utilities are modeled using the logarithm of the allocations, ensuring diminishing returns and promoting fairness. The optimization is subject to constraints ensuring that each issue receives its exact budget, each citizen uses their entire share on preferred issues, and allocations are non-negative.

The problem is solved using CVXPY, a Python library for convex optimization. If a feasible solution is found, the script returns a detailed breakdown of how the budget should be allocated among the issues according to the preferences. If no solution is found, it indicates that no feasible breakdown exists under the given constraints.
