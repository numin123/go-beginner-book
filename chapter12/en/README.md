# Chapter 12: Advanced Topics

## What is this chapter about?
This chapter covers advanced Go techniques and features, such as generics, context, reflection, and code generation—perfect for those who want to go further.

**Example:**
If you want to write functions that accept many types, control execution with cancellation, or generate repetitive code automatically.

## Generics (Go 1.18+)
```go
func Print[T any](v T) {
    fmt.Println(v)
}
Print(123)
Print("hello")
```
Output:
```
123
hello
```

## Context Package
Handle timeout/cancel in goroutines
```go
import (
    "context"
    "time"
    "fmt"
)
ctx, cancel := context.WithTimeout(context.Background(), time.Second)
defer cancel()
select {
case <-ctx.Done():
    fmt.Println("timeout!")
}
```
Output:
```
timeout!
```

## Reflect Package
Inspect/modify types at runtime
```go
import (
    "reflect"
    "fmt"
)
t := reflect.TypeOf(123)
fmt.Println(t.Name())
```
Output:
```
int
```

## Code Generation
Use `go generate` or tools like stringer
Stringer example: [https://pkg.go.dev/golang.org/x/tools/cmd/stringer](https://pkg.go.dev/golang.org/x/tools/cmd/stringer)

[Go Generics](https://go.dev/doc/go1.18#generics)
[Go by Example: Context](https://gobyexample.com/context)
[Go by Example: Reflection](https://gobyexample.com/reflect)
[Go Generate](https://blog.golang.org/generate)

---
