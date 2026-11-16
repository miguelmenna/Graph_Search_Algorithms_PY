# Graph Search Algorithms in Python

A collection of graph search algorithm implementations developed in Python, exploring different strategies for traversing graphs, finding paths, and solving search problems.

This project demonstrates four fundamental search algorithms: **A* Search, Greedy Search, Breadth-First Search (BFS), and Depth-First Search (DFS)**. Each implementation uses a graph represented through an adjacency dictionary and allows users to select starting and destination nodes through a command-line interface.

## 📌 Project Overview

Graph search algorithms are fundamental concepts in computer science and artificial intelligence. They are used to explore relationships between nodes, find paths between locations, and solve problems involving states and transitions.

This project provides practical implementations of different search strategies, allowing their behavior, advantages, and limitations to be explored and compared.

The implementations use a predefined graph containing nodes represented by letters (A–U), with weighted connections between them.

## 🔎 Implemented Algorithms

### 1. A* Search (A-Star)

A* is an informed search algorithm that combines the actual cost of reaching a node with an estimated cost of reaching the destination.

It evaluates nodes using the following function:

\[
f(n) = g(n) + h(n)
\]

Where:

- **g(n):** Actual accumulated cost from the starting node to the current node.
- **h(n):** Heuristic estimate of the remaining cost to the destination.
- **f(n):** Estimated total cost of a path through the current node.

The implementation uses Python's `heapq` module to maintain a priority queue, prioritizing nodes with lower estimated total costs.

**Main characteristics:**
- Uses a priority queue (min-heap).
- Considers accumulated path costs.
- Uses heuristic estimates to guide the search.
- Tracks visited nodes and previously discovered costs.
- Returns the discovered path and the set of visited nodes.

**Important implementation note:** The current heuristic values are predefined for the destination node T. The implementation should be adapted to calculate or receive a heuristic appropriate to the selected destination when searching for other targets. Its optimality also depends on the heuristic properties and graph conditions.

### 2. Greedy Search

Greedy search is an informed search strategy that typically prioritizes the node that appears closest to the destination according to a heuristic function.

In the classical Greedy Best-First Search algorithm, the priority function is:

\[
f(n) = h(n)
\]

Where:

- **h(n):** Estimated cost from the current node to the destination.

The current implementation uses a queue and sorts each node's immediate neighbors according to their edge weights before adding them to the queue.

**Main characteristics of the current implementation:**
- Uses a FIFO queue.
- Sorts neighboring nodes by their immediate edge weights.
- Tracks visited nodes.
- Returns the discovered path and visited nodes.

**Important implementation note:** This implementation is a simplified, locally ordered breadth-first traversal. It does not implement the classical Greedy Best-First Search strategy because it does not use a destination heuristic or globally prioritize the most promising node. A priority queue and a heuristic function would be required for a classical implementation.

### 3. Breadth-First Search (BFS)

Breadth-First Search explores a graph level by level, visiting neighboring nodes before moving to deeper levels.

It uses a FIFO (First In, First Out) queue to determine the exploration order.

**Main characteristics:**
- Uses `collections.deque` as a queue.
- Explores nodes level by level.
- Maintains a collection of visited nodes.
- Records the path from the starting node to the destination.
- Displays the nodes tested during the search.

BFS finds a path with the minimum number of edges in an unweighted graph. When edge weights differ, however, it does not necessarily find the path with the lowest total cost.

### 4. Depth-First Search (DFS)

Depth-First Search explores one branch of a graph as deeply as possible before backtracking and exploring other branches.

The implementation uses a stack (LIFO — Last In, First Out) to manage the nodes awaiting exploration.

**Main characteristics:**
- Uses a stack implemented with a Python list.
- Explores one branch at a time.
- Tracks visited nodes to avoid unnecessary revisits.
- Records attempted paths during the search.
- Returns a path when the destination is found.

DFS is useful for exploring graph structures and understanding traversal strategies. However, it does not guarantee the shortest path.

## ⚙️ Technologies and Concepts

The project uses the following Python features and computer science concepts:

| Technology / Concept | Purpose |
|---|---|
| Python 3 | Main programming language |
| `heapq` | Priority queue for A* |
| `collections.deque` | Efficient FIFO queue for BFS |
| Python Lists | Stack and path management |
| Dictionaries | Graph representation and adjacency lists |
| Sets | Tracking visited nodes |
| Graph Theory | Modeling nodes and connections |
| Heuristic Search | Guiding informed search algorithms |

## 🗺️ Graph Representation

The graph is represented using a Python dictionary, where each key represents a node and its associated dictionary contains neighboring nodes and their corresponding edge weights.

Example:

```python
grafo = {
    'A': {'C': 1},
    'B': {'C': 1, 'D': 1},
    'C': {'A': 1, 'B': 1, 'G': 1}
}
```

In this representation:

- `A`, `B`, and `C` are graph nodes.
- The dictionary keys represent neighboring nodes.
- The associated numbers represent the weights of the connections.

The graph is defined through adjacency dictionaries. Connections and weights are interpreted according to the values explicitly assigned to each node.

## 📊 Algorithm Comparison

| Algorithm | Search Strategy | Main Data Structure | Uses Heuristics? |
|---|---|---|---|
| A* Search | Informed | Priority Queue | Yes |
| Greedy Search | Locally ordered in current implementation | FIFO Queue | No |
| BFS | Breadth-first | FIFO Queue | No |
| DFS | Depth-first | Stack | No |

### Theoretical Complexity

The following table describes the conventional algorithmic complexity under standard graph-search implementations using adjacency lists.

Let:
- **V:** Number of vertices (nodes).
- **E:** Number of edges.

| Algorithm | Time Complexity | Space Complexity |
|---|---|---|
| A* Search | Depends on the graph and heuristic; can be exponential in the worst case | Can be exponential |
| Greedy Best-First Search | Can be exponential in the worst case | Can be exponential |
| BFS | O(V + E) | O(V) |
| DFS | O(V + E) | O(V) |

**Note:** These are theoretical reference complexities, not measured benchmarks of every implementation in this repository. The current implementations include additional path copying, queue operations, and visited-node handling that may affect their practical performance.

## ▶️ Getting Started

### Prerequisites

- Python 3.8 or later.
- No external package installation is required.

The project uses Python standard library modules.

### Running the Algorithms

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/graph-search-algorithms-python.git
```

Navigate to the project directory:

```bash
cd graph-search-algorithms-python
```

Run the desired algorithm using Python:

```bash
python a_star_search.py
```

```bash
python greedy_search.py
```

```bash
python breadth_first_search.py
```

```bash
python depth_first_search.py
```

Each script has its own command-line menu.

The user can select the search operation, enter the starting node, and specify the destination node.

## 💻 Example Interaction

A typical interaction follows this structure:

```text
1: Start Search
2: Exit

Enter your choice: 1

Enter the starting node: A
Enter the destination node: T
```

The program then executes the selected search algorithm and displays the resulting path and, depending on the implementation, the nodes explored during the search.

The exact output and traversal order depend on the selected algorithm.

## 📁 Suggested Project Structure

```text
graph-search-algorithms-python/
│
├── a_star_search.py
├── greedy_search.py
├── breadth_first_search.py
├── depth_first_search.py
│
└── README.md
```

Each Python file contains an independent implementation and can be executed separately.

## 🎯 Learning Objectives

This project explores several important concepts in algorithms, data structures, and artificial intelligence:

- Understanding graph representation through adjacency lists.
- Implementing different graph traversal strategies.
- Working with stacks, queues, and priority queues.
- Understanding informed and uninformed search.
- Exploring heuristic-based pathfinding.
- Comparing algorithmic behavior and complexity.
- Tracking visited nodes and reconstructing paths.
- Understanding the differences between finding a path and finding an optimal path.

## 🚀 Future Improvements

Possible improvements for the project include:

- Implementing a classical Greedy Best-First Search using a heuristic function and priority queue.
- Improving A* to support destination-specific heuristics.
- Adding input validation for starting and destination nodes.
- Calculating and displaying the total path cost.
- Improving path reconstruction using parent dictionaries.
- Avoiding duplicate nodes in search queues.
- Adding automated tests for different graph configurations.
- Supporting user-defined graphs.
- Comparing algorithm performance using execution time and explored-node counts.
- Adding graph visualization to illustrate traversal order and discovered paths.

## 📚 Conclusion

This project demonstrates different approaches to graph search and pathfinding using Python.

By implementing A*, Greedy-style search, Breadth-First Search, and Depth-First Search, it provides an opportunity to understand how different strategies explore graph structures and how their underlying data structures influence their behavior.

The project also highlights an important distinction in algorithm design: finding a valid path does not necessarily mean finding the shortest or least expensive path.

---

**Language:** Python 3  
**Project Category:** Algorithms and Data Structures  
**Main Topics:** Graph Theory, Search Algorithms, Pathfinding, Heuristic Search
