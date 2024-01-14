
# Go Benchmarking Commands

This section explains various commands used for benchmarking in Go, along with their purposes.

## CPU Profiling

1. **Running CPU Benchmarks**:
   ```bash
   go test -bench . -benchtime=10x -run ^$ -cpuprofile cpu00.pprof
   ```
   This command runs benchmarks in your Go tests. 
   - `-bench .` runs all benchmarks.
   - `-benchtime=10x` specifies the benchmark time as 10 iterations.
   - `-run ^$` prevents running any test (only benchmarks).
   - `-cpuprofile cpu00.pprof` writes a CPU profile to the file `cpu00.pprof`.

2. **Analyzing CPU Profile**:
   ```bash
   go tool pprof cpu00.pprof
   ```
   This command launches the pprof tool to analyze the CPU profile.

   Inside the pprof tool, you can use various commands:

   - `top`: Shows the top function calls in terms of CPU time.
     ```bash
     top
     ```

   - `top -cum`: Shows the top function calls, including cumulative data.
     ```bash
     top -cum
     ```

   - `list [function]`: Lists the source code for a specific function, e.g., `csv2float`.
     ```bash
     list csv2float
     ```

   - `web`: Opens a web browser displaying the call graph.
     ```bash
     web
     ```

## Memory Profiling

1. **Running Memory Benchmarks**:
   ```bash
   go test -bench . -benchtime=10x -run ^$ -memprofile mem00.pprof
   ```
   Similar to the CPU profiling command, but with `-memprofile mem00.pprof` to write a memory profile to `mem00.pprof`.

2. **Analyzing Memory Profile (Focusing on Allocation Space)**:
   ```bash
   go tool pprof -alloc_space mem00.pprof
   ```
   Launches pprof for memory profiling, focusing on the allocation space.
