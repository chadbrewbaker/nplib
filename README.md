# nplib
A library of NP problem encodings for SMT solvers.

The [Wikipedia list](https://en.wikipedia.org/wiki/List_of_NP-complete_problems) isn't bad.

[Yurichev's Book](https://sat-smt.codes) is a good introduction to Z3py.

This repository aims at being a comprehensive library of SMT formulations for NP hard problems - with benchmarks across encodings and solver back-ends. To this end I might split out a second repo that has optimized builds of various SMT solver back ends. 

Exact solutions tell what is possible - a baseline to detect performance regressions.

## Design
Intially I would like to stick with z3py. Python lists and dictionaries are easy to serialize from other languages. In the limit I would like Rust/C encodings statically linked to SMT solver binaries.

LLVM IR, eBPF traces, PCAP, and CRIU (Linux Container Images) are common join points in modern software systems - ideally there would be a translation layer to generic SMT encodings.

TLA+, Alloy, and P specifications are a translation layer of interest. 

For streaming IO and linear/quadratic compute I like to use coreutils as a baseline.

## Wanted forumlations
* [Coloring Solvers](https://github.com/llvm/llvm-project/search?q=coloring) for llvm-project, used for register allocation.
* [Codeblock TSP](https://github.com/facebookincubator/BOLT/blob/87e45c91d3dd440021177bc9d37f449db57ecd2d/bolt/src/Passes/ReorderAlgorithm.cpp#L139) for re-ordering ELF and Mach-O files.
* [Memory permutation](https://www.cs.tufts.edu/comp/150CMP/papers/petrank02hardness.pdf) solves for an optimal memory permutation given a list of accessses and a cache cost model. 
* [pahole](https://git.kernel.org/pub/scm/devel/pahole/pahole.git) optimization of C struct ordering to minimize cache misses.
* Profile based reordering of C/C++ files for clang-format - it might even be nice to have comments of hot and cold code.
* SQL schema refactoring - based on a set of queries and data set, it does a bounded refactoring such as splitting off a set of columns to a foreign key, joining tables, or doing datatype reductions on colums then coverting to the output type requested in the query view.
* Optimal solutions to column compression for row blocks in sqlite.
* [OEIS](https://oeis.org) sequences
* Task graph scheduling - especially with AWS spot pricing for batch and "data lake" computations. Most loads you can parameterize by latency, bandwidth, and compute - really cool once AWS Snowball and WASM is in the mix and the scheduler tells you to physically ship storage or bake a WASM file to run local compute.
* Discrete event simulations - package picking, product assembly, delivery optimization, SAAS processing flows,  ... intersection of [probabilistic programming](https://github.com/getguesstimate/guesstimate-app) and SMT solving.
* Speeding up Machine Learning - exactly solving bounded resource formulations so you have error estimates with lossy optimizers.
