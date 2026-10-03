# SLE-3_IAI

# 8-Puzzle Search Solver & Profiler

An Artificial Intelligence project that solves the **8-Puzzle problem** using uninformed search algorithms and compares their performance.

The project implements:

* Breadth-First Search (BFS)
* Depth-Limited Depth-First Search (DFS)
* Node expansion counting
* Execution-time measurement
* Automated experiments and result storage

## Project Overview

The system takes a scrambled **3×3 sliding-tile puzzle** and searches for a sequence of moves that reaches the goal state.

The project was developed across SLE-1, SLE-2, and SLE-3:

* **SLE-1:** Implementation of the 8-Puzzle search solver
* **SLE-2:** Performance profiling and comparison
* **SLE-3:** Architectural design using the C4 model

BFS and DFS use the same problem representation and neighbor-generation logic so that their search strategies can be compared fairly.

## Algorithms

### Breadth-First Search (BFS)

BFS explores states level by level using a queue.

It is used to find shortest solution paths for the tested puzzles.

### Depth-Limited Depth-First Search (DFS)

DFS explores states using a stack and has a depth limit of **30**.

Unlike BFS, DFS does not necessarily return the shortest solution path.

## System Architecture

The project is organized into six major containers:

1. **Input Module** – receives the scrambled puzzle.
2. **Problem Definition** – stores the board representation, goal state, and legal moves.
3. **Search Engine** – executes BFS or DFS.
4. **Visited Set** – prevents repeated exploration of states.
5. **Output Module** – reports solution and performance metrics.
6. **Profiling Driver** – runs experiments and records execution times and node counts.

### Code-Level Components

Important functions/classes include:

* `State` / `Node`
* `is_goal()`
* `get_neighbors(state)`
* `bfs(start)`
* `dfs(start, limit=30)`
* `reconstruct_path(node)`
* `run_experiments()`

## Performance Profiling

The profiling driver runs each algorithm **5 times on each of 3 test puzzles**.

Execution time is measured using Python's:

```python
time.perf_counter()
```

The experiment results are saved in:

```text
results.json
```

The project also uses `py-spy` for runtime sampling during profiling.

## Example Results

For the tested puzzles, BFS found solution paths of:

* 4 moves
* 12 moves
* 18 moves

The depth-limited DFS implementation returned 30-move paths for these tests.

These results demonstrate the difference between breadth-first and depth-limited depth-first exploration.

## Repository Structure

A typical repository structure is:

```text
SLE-3_IAI/
│
├── README.md
├── AI_CONTRIBUTION.md
├── results.json
├── *.py
└── diagrams/
```

## Future Improvements

Possible future extensions include:

* Adding an **A*** search implementation
* Adding a heuristic module
* Comparing BFS, DFS, and A*
* Improving visualization of the search process
* Extending the profiler with additional performance metrics




