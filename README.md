# DiceDB Test Suite

This repository contains a suite of unit and integration tests for the [DiceDB project](https://github.com/DiceDB/dice). The tests cover various features and functionalities of the system, ensuring both correctness and performance.

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Running the Test Suite](#running-the-test-suite)
- [Cleaning Up](#cleaning-up)
- [Contributing](#contributing)

## Overview

The DiceDB test suite consists of:

- **Unit Tests**: Validating individual components of the system.
- **Integration Tests**: Testing the interaction between components.
  
The suite leverages TCL (Tool Command Language) for testing, and it can be executed locally with minimal setup. The script automates server setup, running tests, and teardown.

## Prerequisites

Before running the test suite, ensure the following tools are installed on your system:

- [Git](https://git-scm.com/) (for cloning the repository)
- [Go](https://golang.org/doc/install) (for running the server)
- [Air](https://github.com/cosmtrek/air) (optional, for hot-reloading the Go server)
- TCL (for running the tests)

To install Go and Git:

```bash
# Install Git
sudo apt-get install git

# Install Go
sudo apt install golang-go

# Install air
go install github.com/cosmtrek/air@latest
```

## Setup

### Apply Patch (if necessary)

A patch allows you to modify the dice repository's code without permanently changing the source files in the master branch. It's useful for testing features, fixing bugs, or adjusting configurations temporarily.

head over to the `dice-patch` folder and make modifications if required to ignore any commands while running the test suite.

## Running the Test Suite

To run the test suite, just execute the binary `tcltest`, It will automatically do following steps:

1. Clone the dice [repository](git@github.com:DiceDB/dice.git)
2. It applies patch on the cloned repository to do modifications before running the test suite
3. Test suite automatically starts the DiceDB server using `air` command in the background and waits till the serve starts successfully.
4. It then runs configures and runs the tcl tests available in the `/tcltests/unit` and `/tcltests/integration`subdirectories using the following command:

  ```sh
  ./runtest --host 0.0.0.0 --port 7379 --tags -needs:debug --tags -cluster:skip --singledb --ignore-encoding
  ```

## Cleaning Up

Once the test suite has finished running:

- The server will be stopped automatically.
- If the repository was cloned for testing purposes, it will be removed after the tests.

## Contributing

We welcome contributions to the test suite. if you would like to add more test coverage, head over to the redis repository and check the  and [integration] subdirectories under the tests folder.

We welcome and encourage contributions to enhance the DiceDB test suite. Whether you're improving existing tests or adding new ones, your efforts help make the project more robust.

If you're looking to expand test coverage or contribute new tests, we recommend checking out the Redis repository for inspiration, particularly in the areas of [unit tests](https://github.com/redis/redis/tree/unstable/tests/unit) and [integration tests](https://github.com/redis/redis/tree/unstable/tests/integration).

Add your new tests or improve existing ones in the appropriate test directories. Once you’ve completed your changes, push your branch to GitHub and open a pull request against the main repository. Ensure your PR includes a clear description of the changes made.
