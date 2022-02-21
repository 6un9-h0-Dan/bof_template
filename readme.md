# BOF Template

This repository is meant to host the core files needed to create a Beacon Object File for use with Cobalt Strike.

A Beacon Object File (BOF) is a compiled C program, written to a convention that allows it to execute within a Beacon process and use internal Beacon APIs. BOFs are a way to rapidly extend the Beacon agent with new post-exploitation features.

## beacon.h

beacon.h contains definitions for several internal Beacon APIs. The function go is similar to main in any other C program. It's the function that's called by inline-execute and arguments are passed to it. BeaconOutput is an internal Beacon API to send output to the operator.

## tests

The tests directory contains examples for using the internal Beacon APIs.  The directory contains the following:
- build.sh - builds the object files located in tests/src. Requires mingw-w64 cross-compiler package
- bof_test_runner.cna - Aggressor script file for running the tests
- src directory - Contains example source files for using the internal Beacon APIs.

How to execute the tests:
1. Build the object files with the build.sh script in the tests directory.
2. Start a team server and client
3. Load the bof_test_runner.cna script from the tests directory.
4. Generate and start a beacon on a test system.
5. In the beacon console execute: run_boff_tests "<user_string>" \<numeric\> "<numeric_string>"

where:  
&emsp; user_string is any quoted input string  
&emsp; numeric is any signed short or integer value  
&emsp; numeric_string is any quoted numeric string (only used in testBeaconDataLongLong) 

## BOF Documentation

- https://www.cobaltstrike.com/help-beacon-object-files

## Community developed BOFs

- https://cobalt-strike.github.io/community_kit/

