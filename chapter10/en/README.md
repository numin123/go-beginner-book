# Chapter 10: Testing & Debugging

## What is this chapter about?
This chapter teaches you how to check if your program works correctly by writing tests, and how to fix errors (debugging) to make sure your program runs as expected.

**Example:**
If you want to know whether your code works as intended, or want to find bugs in your program.

## Writing Unit Tests
Use the `testing` package
```go
import "testing"
func add(a, b int) int { return a + b }
func TestAdd(t *testing.T) {
    got := add(2, 3)
    if got != 5 {
        t.Errorf("want 5 got %d", got)
    }
}
```
Output (when running `go test`):
```
PASS
```

## Writing Benchmark Tests
```go
func BenchmarkAdd(b *testing.B) {
    for i := 0; i < b.N; i++ {
        add(2, 3)
    }
}
```
Output (when running `go test -bench .`):
```
BenchmarkAdd-8   1000000000   0.25 ns/op
```

## Debugging
Use Delve (dlv)
- Install: `go install github.com/go-delve/delve/cmd/dlv@latest`
- Use: `dlv debug`
Example of setting a breakpoint:
```
dlv debug
(dlv) break main.go:5
(dlv) continue
```

[Go by Example: Testing](https://gobyexample.com/testing-and-benchmarking)
[Delve Debugger](https://github.com/go-delve/delve)

---
