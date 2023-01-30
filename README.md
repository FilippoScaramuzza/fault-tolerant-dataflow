# Fault-Tolerant Dataflow Platform
Fault-tolerant dataflow platform implementation for the distributed systems course of the Polytechnic of Milan.

## Project Description
The platform is implemented for processing key-value pairs where keys and values are integers. The platform offers three operators, which are executed independently and in parallel for each key `k`:
- `map(f: int -> int)`: for each input tuple `<k, v>`, it outputs a tuple `<k, f(v)>`
- `changeKey(f: int -> int)`: for each input tuple `<k, v>`, it outputs a tuple `<f(v), v>`
- `reduce(f: list<int> -> int)`: takes in input the list `V` of all values for key `k`, and outputs `<k, f(V)>`

The platform includes a **coordinator** and multiple **workers**. The coordinator accepts **dataflow programs** specified as an arbitrarily long sequence of the above operators. Programs are defined in a JSON file provided as input. Each operator is executed in parallel over multiple partitions of the input data, where the number of partitions is specified as part of the dataflow program. The coordinator splits the input data among processes and sends the operations set. Input data is split among processes based on the key. Thanks to this approach key-value pairs with the same key are located into the same process.

The systems implements a fault-tolerance mechanism that limit the amount of work that needs to be be re-executed in the case a worker fails. This is achieved by saving a dump file containing the partial results computed until the failure. The coordinator keeps track of the operations computed by each worker and then tells it the point in the operations set it executed.

The project uses [Open MPI](https://www.open-mpi.org) and [mpi4py](https://mpi4py.readthedocs.io/en/stable/) as middleware for distributed computing.

## Setup Guide
Conda setup

## How to Run
Run instruction

## Run in distributed environment
Setup ssh connection
