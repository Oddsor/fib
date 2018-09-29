# Recursive Fibonacci Benchmark using top languages on Github

Top 10: JavaScript, Java, Python, Ruby, Php, C++, C#, C, Go [reference](http://www.techworm.net/2016/09/top-10-popular-programming-languages-github.html)

Others: Crystal, Rust, Swift, Mono, Elixir, Perl, R, Julia, D, Nim

This code performs a recursive fibonacci to the 46th position with the result of 2,971,215,073.

All tests are run on:
 - iMac (Retina 5K, 27-inch, Late 2015)
 - OS: macOS High Sierra 10.13.6
 - Processor: 3.2 GHz Intel Core i5
 - Memory: 16 GB 1867 MHz DDR3

Running Python
Last benchmark was ran on September 29, 2018

## Natively compiled, statically typed

| Language   | Time, s   | Compile                                      | Run          |
|------------|-----------|----------------------------------------------|--------------|
| Nim        |    4.677 | nim cpp -d:release fib.nim                    | time ./fib   |
| C          |    5.382 | gcc -O3 -o fib fib.c                          | time ./fib   |
| Crystal    |    5.803 | crystal build --release fib.cr                | time ./fib   |
| C++        |    6.099 | g++ -O3 -o fib fib.cpp                        | time ./fib   |
| Fortran    |    6.136 | gfortran -O3 -o fib fib.f03                   | time ./fib   |
| Rust       |    6.590 | rustc -O fib.rs                               | time ./fib   |
| D          |    7.175 | ldc2 -O3 -release -flto=full -of=fib fib.d    | time ./fib   |
| Haskell    |    8.151 | ghc -O3 -o fib fib.hs                         | time ./fib   |
| OCaml      |    9.607 | ocamlopt -O3 -o fib fib.ml                    | time ./fib   |
| Swift      |   10.786 | swiftc -O -g fib.swift                        | time ./fib   |
| Go         |   10.923 | go build fib.go                               | time ./fib   |

## VM compiled bytecode, statically typed

| Language  | Time, s | Compile                            | Run                         |
|-----------|---------|------------------------------------|-----------------------------|
| Java      |    7.709 | javac Fib.java                       | time java Fib               |
| C#        |    7.801 | dotnet build -c Release -o ./bin     | time dotnet ./bin/fib.dll   |
| C# (Mono) |   12.143 | mcs fib.cs                           | time mono fib.exe           |

## VM compiled before execution, mixed/dynamically typed

| Language  | Time, s | Run                         |
|-----------|---------|-----------------------------|
| Dart      |    9.449 | time dart fib.dart          |
| Julia     |   11.148 | time julia -O3 fib.jl       |
| Node      |   19.351 | time node fib.js            |
| Elixir    |   73.796 | time elixir fib.exs         |

NOTE: These languages include compilation time which should be taken into consideration when comparing.

## Interpreted, dynamically typed

| Language  | Time, s | Run                         |
|-----------|---------|-----------------------------|
| Php       |  198.279 | time php fib.php           |
| Ruby      |  202.901 | time ruby fib.rb           |
| Python    |  512.621 | time python fib.py         |
| Python3   |  758.681 | `time python3 fib.py`      |
| Perl      | 1133.131 | `time perl fib.pl`         |
| Perl 6    |     TODO | `time perl6 fib.p6`        |
| Tcl       |     TODO | `time tclsh fib.tcl`       |
| R         | 1796.495 | `time r -f fib.r`          |

## Optimized code that breaks the benchmark

The following code examples use techniques that break the benchmark. They do not perform the same internal tasks as the other examples
so are not a good apples to apples comparisons. It demonstrates that all benchmarks will have some caveat.

| Language                | Time, s  | Compile                              | Run                         |
|-------------------------|----------|--------------------------------------|-----------------------------|
| Go (mem)                |  0.005*  | `go build -o fib fib-mem.go`         | `time ./fib`                |
| Nim (mem)               |  0.006*  | `nim cpp -d:release fib_mem.nim`     | `time ./fib_mem`            |
| C++ (constexpr)         |  0.086*  | `g++-8 -O3 -o fib fib-constexpr.cpp` | `time ./fib`                |
| Node (mem)              |  0.112*  |                                      | `time node fib-mem.js`      |
| Python (lru_cache)      |  TODO    |                                      | `time python3 fib-cache.pu` |
| Lua (mem)               |  TODO    |                                      | `time luajit fib-mem.lua`   |

**NOTE:**
The C++ (constexpr) is using a `constexpr` which optimizes the recursive call to a constant. It was provided by [Ole Christian Eidheim](https://gitlab.com/eidheim).
The Go (mem) is using memoization.  It was provided by [Alexander F. Rødseth](https://github.com/xyproto).
The Node (mem) is another example using memoization.  It was provided by [YSTYLE-L.X.Y](https://github.com/ystyle)
The Nim (mem) version is provided by [PMunch](https://github.com/PMunch)

## Versions

- go version go1.11 darwin/amd64
- g++-8 (Homebrew GCC 8.2.0) 8.2.0
- crystal Crystal 0.26.1 (2018-08-27) LLVM: 6.0.1
- g++ Apple LLVM version 10.0.0 (clang-1000.11.45.2)
- gcc Apple LLVM version 10.0.0 (clang-1000.11.45.2)
- nim Nim Compiler Version 0.18.0 [MacOSX: amd64]
- swiftc Apple Swift version 4.2 (swiftlang-1000.11.37.1 clang-1000.11.45.1)
- rustc 1.29.0
- javac 10.0.1
- mcs Mono C# compiler version 5.12.0.226
- dotnet 2.1.4
- dart Dart VM version: 2.0.0 (Fri Aug 3 10:53:23 2018 +0200)
- julia version 0.6.3
- node v9.4.0
- elixir Elixir 1.7.3 (compiled with Erlang/OTP 21)
- ruby 2.5.1p57 (2018-03-29 revision 63029)
- php 7.1.16 (cli) (built: Apr  1 2018 13:14:42)
- python 2.7.15
- python3 3.7.0
- perl 5, version 26, subversion 2 (v5.26.2)
- perl6 This is Rakudo Star version 2018.06 built on MoarVM version 2018.06
- r version 3.5.0 (2018-04-23)
- lcd2 the LLVM D compiler (1.11.0)
- ocaml The OCaml toplevel, version 4.07.0
- ghc The Glorious Glasgow Haskell Compilation System, version 8.4.3
- gfortran GNU Fortran (Homebrew GCC 8.2.0) 8.2.0
- tchsh 8.5

## Caveats

[Fibonacci Benchmark](https://crystal-lang.org/2016/07/15/fibonacci-benchmark.html)
