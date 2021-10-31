# Monte Carlo Tree Search (MCTS)
## Who invented MCTS?
In 2006, Rémi Coulom combined Monte Carlo method to game-tree search and coined the name MCTS. [^1]

## What is MCTS?
MCTS is an any-time that combines Monte Carlo simulations and Tree Search algorithms in order to determine which move in a given state leads to the highest average utility.

## How does it work?
### Overview
It works by growing a game tree where each node represents a game state, starting with the current state as a root node. 

First, it **selects** the most "lucrative" leaf node. Then it **expands** that leaf node by adding a child node, where the edge between them is a legal move of the game. Then the game is **simulated** to the end - starting from the child node's game state - resulting in either a win or a loss. Finally, child node stores the result, and the result **backpropagates** recursively to its parent, its parent's parent, and so on until the root node.

In the backpropagation step, each predecessor node of the child increments the number of times it has been visited and updates its score. The score divided by the number of visits is the **average utility** of the node (i.e. how good it is on average to make that move).

This repeats until time runs out. When it does, it chooses the move that results in the child with the highest average utility.

### Select
Deciding which leaf node to select (the **selection policy**) depends heavily on the domain. It is the classic Exploration vs Exploitation problem: how do we know which moves are worth "thinking" about?

UCB1
### Expand
### Simulate
## When to use it?
It is used when:
- A game is new or not well studied
- Game is unsuited to Minimax.
    - The game state-space is too large (branching factor is high).
    - The decision points in a game lead to various different states.
- There aren't any good evaluation functions for the states of a game.
    -   Likelihood of winning is not obvious given current observable game state.
    -   Imperfect Information games.
    -   Non Zero-Sum games.
    -   Preferences (i.e. utility function) of other agents are unknown.
-   The terminal states of the game (win/loss) is determined by the rules of the game.
-   A simulation of the game is cheap to compute.

## Where is it used?
It is mainly used in game playing, but can be used as a component of more complex techniques in AI, such as Reinforcement Learning algorithms, which is cutting edge in AI.

## How does it perform?
### Time Complexity
### Space Complexity
### Correctness

### Bibliography
[^1]: [Rémi Coulom](https://en.wikipedia.org/wiki/R%C2%A9mi_Coulom) (2007). "Efficient Selectivity and Backup Operators in Monte-Carlo Tree Search". _Computers and Games, 5th International Conference, CG 2006, Turin, Italy, May 29–31, 2006.
