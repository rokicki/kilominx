This repository is data and code for the paper "Notes on the Kilominx"
by Tomas Rokicki, submitted to the Gathering for Gardner 16 held in
February 2026.

Everything here was executed on Mac OSX from the command line.  Using
Linux should nearly identical.  You may have to adjust -M options to
suit the memory of your machine (I recommend using half the physical
memory).

We assume this directory can be invoked with ~/kilominx, and that
https://github.com/cubing/cubing.js and https://github.com/twsearch
are cloned into ~/cubing.js and ~/twsearch, respectively.  We assume
you have a C++ compiler to compile twsearch and that you have installed
bun.

To build cubing.js, cd into that directory and type

	make setup
	make build

To build twsearch, cd into that directory and type

	make

The first thing we need to do is create some files for twsearch to use.
To do this, make sure you are in the cubing.js directory (to help
bun find its files).  The kilominx is not one of the predefined puzzles
in cubing.js, but it is just a megaminx without centers or edges.  So we
can create a basic kilominx file for twsearch with the following command:

	bun src/bin/puzzle-geometry-bin.ts --ksolve --rotations --optimize --nocenters --noedges megaminx > ~/kilominx/kilominx.tws

We say we want a ksolve file (which is the base of the tws file format),
and we want all the rotations of the puzzle, and we'd like it to simplify
if it can, and we don't want centers or edges.

You can also ask cubing.js what the state space of the kilominx is, with

	bun src/bin/puzzle-geometry-bin.ts --ss --nocenters --noedges megaminx

and on the last line we see the value 1.413.834.128.545.313.800.765,440,000
which is 1.4e27, the size of the large group, which considers only a single
rotation of the puzzle to be solved.
