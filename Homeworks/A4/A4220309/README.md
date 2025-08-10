
# Routing Protocols Simulation (DVR and LSR)

## Overview
This project implements two fundamental routing algorithms: **Distance Vector Routing (DVR)** and **Link State Routing (LSR)**. The program simulates these algorithms on a network represented by an adjacency matrix, computing the shortest paths between nodes and generating routing tables for each node. The implementation is written in C++ and takes an input file specifying the network topology to produce routing tables showing destination nodes, costs, and next hops.

## Team Member
- **Chayan Kumawat** (Roll Number: 220309)

## Files
- **`routing_sim.cpp`**: The main C++ source file containing the implementation of DVR and LSR algorithms. It reads an adjacency matrix from an input file, simulates both routing protocols, and outputs the routing tables.
- **`Makefile`**: A build script to compile the C++ program. Running `make` generates the executable.
- **`inputfile.txt`**: An example input file specifying the network topology as an adjacency matrix. Additional input files can be used in the same format.
- **`README.md`**: This file, providing an overview and instructions for the project.

## Prerequisites
- **C++ Compiler**: A C++ compiler such as `g++` (C++11 or later) is required to compile the program.
- **Make**: The `make` utility is needed to build the project using the provided Makefile.
- **Operating System**: The program is platform-independent but has been tested on Unix-like systems (Linux/macOS). Windows users may need a compatible environment like WSL or MinGW.
- **Input File**: An input file in the correct format (described below) is required to specify the network topology.

## How to Run

1. **Clone the Repository**: Download the project files from the GitHub repository: [https://github.com/privacy-iitk/cs425-2025.git](https://github.com/privacy-iitk/cs425-2025.git).

2. **Navigate to the Project Directory**: Change to the directory containing the project files.

3. **Compile the Program**: Run the following command to compile the program using the Makefile:
    ```bash
    make
    ```
    This generates an executable named `routing_sim`.

4. **Run the Program**: Execute the program by providing an input file as a command-line argument. For example:
    ```bash
    ./routing_sim inputfile.txt
    ```

5. **View Output**: The program outputs the routing tables for both DVR and LSR simulations to the console, showing the destination, cost, and next hop for each node.

## Input File Format
The input file specifies the network topology as an adjacency matrix. The format is as follows:

- **First Line**: An integer `n`, representing the number of nodes in the network.
- **Next `n` Lines**: Each line contains `n` space-separated integers, representing the adjacency matrix. The entry in the `i`th row and `j`th column specifies the cost (e.g., latency, bandwidth) of the link between node `i` and node `j`.
  - A value of `0` indicates no link or the node itself (diagonal entries).
  - A value of `9999` represents an unreachable link (infinite cost).

### Example Input File (`inputfile.txt`):
```
4
0 10 100 30
10 0 20 40
100 20 0 10
30 40 10 0
```
This represents a network with 4 nodes, where the matrix specifies the link costs between them.

## Output Format
The program outputs routing tables for each node for both DVR and LSR simulations. The output is divided into two sections:

### Distance Vector Routing Simulation
For each node, a routing table is printed with the following columns:
- **Dest**: Destination node ID.
- **Cost**: The computed cost to reach the destination.
- **Next Hop**: The next node in the path to the destination (`-` if unreachable or the node itself).

#### Example:
```
--- Distance Vector Routing Simulation ---
Node 0 Routing Table:
Dest    Cost    Next Hop
0       0       -
1       10      1
2       30      3
3       30      3
```

### Link State Routing Simulation
For each node, a routing table is printed with the same columns as above, excluding the node itself as a destination.

#### Example:
```
--- Link State Routing Simulation ---
Node 0 Routing Table:
Dest    Cost    Next Hop
1       10      1
2       30      3
3       30      3
```

The tables reflect the shortest paths computed by the DVR (using Bellman-Ford) and LSR (using Dijkstra’s algorithm) algorithms.

