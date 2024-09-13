# How to add new tests in the suite?

## Table of Contents

- [About TCL tests](#about)
- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Running the Test Suite](#running-the-test-suite)
- [Cleaning Up](#cleaning-up)
- [Contributing](#contributing)

## About

TCL tests refer to automated tests written in the Tcl (Tool Command Language) scripting language, commonly used for testing software applications, especially in environments where Tcl is used for scripting or automation. Tcl tests can include unit tests, integration tests, regression tests, or functional tests, depending on the scope and purpose.

## Idnetify tcl tests from Redis repository

To make DiceDB as a drop in replacement for Redis along with all the other features, we try to make it maximum compatible with the exisiting redis features. The best way to check the compatibility is running the redis tests against DiceDB.

Steps to replicate the tests from Redis repository in the Dice DB tcl test suite:

1. [Setup Redis 7.2.5 locally](https://gist.github.com/arpitbbhayani/94aedf279349303ed7394197976b6843)
2. Navigate to the [tests](https://github.com/redis/redis/tree/unstable/tests) directory.
3. Check Dice [supported commands](https://github.com/DiceDB/dice/blob/master/internal/eval/commands.go)
4. Check the relevant {test}.tcl file from the tests folder in the redis repository. (Try to focus on the integrations and unit test files)
5. Copy the contents of the files into the [Dice DB tcltests directory](https://github.com/AshwinKul28/dice-tests/tree/main/tcltests) in the relevant folder. (Please maintain the same folder structure as Redis tests directory)
6. If you have added any other tests apart from integration/unit then create the subdirectory in the tcltests folder and add the subdirectory name in the [test helper file](https://github.com/AshwinKul28/dice-tests/blob/main/tcltests/test_helper.tcl#L23)
7. Requirements for setting up tcl test suite are mentioned [here](https://github.com/AshwinKul28/dice-tests/blob/main/README.md#prerequisites)
8. Run the TCL tests from the parent directory using tcltest binary (cmd: `./tcltest`)
9. The test suite will automatically create a txt file mentioning description for the failed test cases
10. To create issues in the Dice Repository follow the template and copy the contents from the txt file created.