# ExpNo:10 Implementation of Classical Planning Algorithm
# Algorithm or Steps Involved:
<ol>
  <li>Define the initial state</li>
  <li>Define the goal state</li>
  <li>Define the actions</li>
  <li>Find a <b>plan</b> to reach the goal state</li>
  <li>Print the plan</li>
</ol>

# Example - 1
```
initial_state = {'A': 'Table', 'B': 'Table'}
goal_state = {'A': 'B', 'B': 'Table'}

actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}},
    'move_B_to_Table': {'precondition': {'A': 'Table', 'B': 'B'}, 'effect': {'B': 'Table'}}
}

plan = find_plan(initial_state, goal_state, actions)
print(plan)
```
# Output:
```
['move_A_to_B']
```
# Example - 2
```
initial_state = {'A': 'Table', 'B': 'Table', 'C': 'Table'}
goal_state = {'A': 'B', 'B': 'C', 'C': 'Table'}

actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}},
    'move_B_to_C': {'precondition': {'A': 'B', 'B': 'Table', 'C': 'Table'}, 'effect': {'B': 'C'}},
    'move_C_to_Table': {'precondition': {'A': 'B', 'B': 'C', 'C': 'C'}, 'effect': {'C': 'Table'}}
}

plan = find_plan(initial_state, goal_state, actions)
print(plan)
```
# Output:
```
['move_A_to_B', 'move_B_to_C']
```
# PROGRAM :

```
def find_plan(initial, goal, actions):
    state = initial.copy()
    plan = []

    while not all(state.get(k) == v for k, v in goal.items()):
        for name, action in actions.items():
            if all(state.get(k) == v for k, v in action["precondition"].items()):
                for k, v in action["effect"].items():
                    state[k] = v
                plan.append(name)
                break
        else:
            return "No plan found"

    return plan


# Example 1
initial = {'A': 'Table', 'B': 'Table'}
goal = {'A': 'B', 'B': 'Table'}

actions = {
    'move_A_to_B': {
        'precondition': {'A': 'Table', 'B': 'Table'},
        'effect': {'A': 'B'}
    }
}

print("Example 1:", find_plan(initial, goal, actions))


# Example 2
initial = {'A': 'Table', 'B': 'Table', 'C': 'Table'}
goal = {'A': 'B', 'B': 'C', 'C': 'Table'}

actions = {
    'move_A_to_B': {
        'precondition': {'A': 'Table', 'B': 'Table'},
        'effect': {'A': 'B'}
    },
    'move_B_to_C': {
        'precondition': {'A': 'B', 'B': 'Table', 'C': 'Table'},
        'effect': {'B': 'C'}
    }
}

print("Example 2:", find_plan(initial, goal, actions))
```
# OUTPUT:

<img width="817" height="295" alt="image" src="https://github.com/user-attachments/assets/810d7897-82e4-48a4-b231-b9affd8f5aea" />

## RESULT:

We got the Output Successfully

# Please Prepare Solution or Definition For the method find_plan(initial_state, goal_state, actions)
<h3>You Can use any of the searching Strategies for planning and executing a sequence of actions.<br> You can also look in to the Code given in the Repository.</h3>
