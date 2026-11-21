# Zylenox CP Library

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Language: C++](https://img.shields.io/badge/language-C%2B%2B-00599C.svg)](#)
[![Codeforces](https://img.shields.io/badge/Codeforces-Zylenox-1F8ACB.svg)](https://codeforces.com/profile/Zylenox)

A lightweight, feature-rich **competitive programming** toolkit in C++, built for speed, efficiency and clean implementations during contests.

It combines three things in one repository:

- a **contest template** with a debugging helper,
- a **personal notebook** of short, battle-tested algorithms,
- a **large reference library** of 390+ advanced algorithms and data structures.

---

## Table of Contents

- [Quick Start](#quick-start)
- [Repository Structure](#repository-structure)
- [Contest Template](#contest-template)
- [Debugging](#debugging)
- [Stress Testing](#stress-testing)
- [Personal Notebook](#personal-notebook)
- [Reference Library](#reference-library)
- [Credits](#credits)
- [License](#license)

---

## Quick Start

```bash
git clone https://github.com/spirizdev/cp-library.git
cd cp-library
```

Copy `template.cpp` and `debug.cpp` into your working folder, then compile with the `LOCAL` flag to enable debug output:

```bash
# Local: debug output enabled
g++ -std=c++17 -O2 -DLOCAL template.cpp -o sol

# Judge-like: debug calls compile to nothing
g++ -std=c++17 -O2 template.cpp -o sol
```

---

## Repository Structure

```text
zylenox/
├── template.cpp          # Main contest template
├── debug.cpp             # Debug printer (only active with -DLOCAL)
├── hash_function.cpp     # Custom hashes for pair / tuple / vector
├── data-structures/      # Fenwick, segment trees, DSU, Mo's, HLD, tries, ...
├── dp/                   # CHT, digit DP, SOS DP, Knuth, inclusion-exclusion
├── geometry/             # 2D / 3D geometry, convex hull
├── graph-theory/         # Shortest paths, flows, SCC, LCA, MST, matching, ...
├── math/                 # Binary power, Euler phi, modular inverse, matrices
├── strings/              # Hashing, KMP, Z, Manacher, suffix array, tries
├── miscelleneous/        # Big integer, parallel binary search
├── stress_testing/       # Generators, checker and Windows batch scripts
├── code-library-main/    # Extended reference library (390+ files)
└── LICENSE
```

---

## Contest Template

`template.cpp` is a ready-to-use skeleton with:

- **Short macros:** `fi`, `se`, `pb`, `eb`, `all(x)`, `rall(x)`, `sz(x)`, `bit(i, x)`, `mem(a, b)`
- **Loop helpers:** `rep(i, a, b)`, `per(i, a, b)`, `each(x, a)`, plus `ntest` for multi-test input
- **Type aliases:** `ll`, `db`, `pii`, `pll`, `vi`, `vl`, `vvi`, `vvl`, ...
- **`#define int ll`** so integers are 64-bit by default
- **Seeded RNG:** `mt19937_64 rng` seeded from the clock
- **Helpers:** `cmax`, `cmin`, and a safe `__lcm`
- **Automatic file I/O:** reads `input.inp` if it exists, otherwise `task.inp` / `task.out`, otherwise stays on standard input and output
- **Timer:** prints elapsed time to `stderr` at the end of the run

---

## Debugging

`debug.cpp` is included only when `LOCAL` is defined, so it never affects your submission.

```cpp
vector<int> a = {1, 2, 3};
map<int, string> m = {{1, "a"}, {2, "b"}};

debug(a, m);        // prints the line number, variable names and values
debugArr(arr, n);   // prints the first n elements of a C-style array
```

It can print primitives, strings, bitsets, vectors, pairs, tuples, sets, maps and nested containers. Without `-DLOCAL`, both macros expand to `void()`.

---

## Stress Testing

The `stress_testing/` folder helps you find a failing test by comparing a solution against a trusted one on random input.

| File | Purpose |
| --- | --- |
| `gen.cpp` | Random test generator |
| `tree.cpp`, `graph.cpp` | Random tree / graph generators |
| `my.cpp` | The solution being tested |
| `correct.cpp` | A brute-force or known-correct solution |
| `checker.cpp` | Custom checker, for problems with multiple valid answers |
| `script.bat` | Loop: `gen` → `my` and `correct` → compare outputs |
| `script_checker.bat` | Loop: `gen` → `my` → `checker` |
| `script_tree.bat` | Same as `script.bat`, using the tree generator |
| `script_graph.bat` | Same as `script.bat`, using the graph generator |

Run a script, and it stops at the first mismatch. The failing input is saved in `input.txt`, and the two outputs in `my.txt` and `correct.txt`.

> The scripts are written for **Windows** and assume MinGW at `C:\Program Files\CodeBlocks\MinGW\bin`. Edit the `PATH` line at the top of each `.bat` file if your compiler is elsewhere.

---

## Personal Notebook

Short implementations that are quick to copy during a contest.

| Folder | Contents |
| --- | --- |
| `data-structures` | Fenwick tree (1D / 2D), segment tree (including dynamic), DSU with rollback, Mo's algorithm (plain, with updates, online, on tree), HLD, centroid decomposition, sparse table / RMQ (1D / 2D), sqrt decomposition, tries |
| `dp` | Convex hull trick, digit DP, SOS DP, Knuth optimization, inclusion-exclusion |
| `geometry` | 2D and 3D geometry, convex hull |
| `graph-theory` | Dijkstra, SPFA, Floyd, MST, SCC (Kosaraju / Tarjan), bridge tree, 2-edge-connected components, topological sort, LCA, virtual tree, max flow, min-cost max-flow, max matching, Steiner tree, sweep line |
| `math` | Binary exponentiation, Euler's totient, modular inverse, matrices |
| `strings` | String hashing, KMP, Z-function, Manacher, suffix array, tries |
| `miscelleneous` | Big integer, parallel binary search |

---

## Reference Library

`code-library-main/` is a much larger collection of advanced algorithms, organized by topic.

| Category | Files | Highlights |
| --- | ---: | --- |
| Basics | 17 | Sorting, binary search, prefix sums, bit tricks, two pointers |
| Data Structures | 62 | Segment tree beats, persistent structures, link-cut tree, top tree, treaps, wavelet tree, KD tree, Mo's variants, sqrt tree |
| Dynamic Programming Optimizations | 22 | Li Chao tree, Knuth, divide and conquer, CHT variants, SOS convolutions, Hirschberg |
| Game Theory | 4 | Alpha-beta pruning, Hackenbush |
| Geometry | 13 | Delaunay, Voronoi, half-plane intersection, point location, 2D / 3D toolkits |
| Graph Theory | 90 | Blossom, flows, block-cut tree, cactus, chordal graphs, 2-SAT / 3-SAT, Chinese postman |
| Math | 60 | FFT, NTT, FWHT, Berlekamp-Massey, determinants, linear recurrences, simplex, polynomials |
| Number Theory | 73 | Miller-Rabin, Pollard rho, discrete log / root, Min_25 sieve, floor sums, CRT, Diophantine equations |
| Strings | 24 | Suffix automaton, suffix array, palindromic tree, Aho-Corasick, hashing, Z / KMP |
| Miscellaneous | 25 | Matroid intersection, Josephus, expression parsing, Schreier-Sims, bitset utilities |

Files are named after the algorithm they implement, so you can find them with your editor's file search or `ls`.

---

## Credits

Everything outside `code-library-main/` is my own contest notebook. The `code-library-main/` folder is a collection of implementations gathered from public competitive-programming libraries. Credit belongs to the original authors.

---

## License

This project is licensed under the [MIT License](LICENSE).

---

*One more WA, one step closer to AC.*
