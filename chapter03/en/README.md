# Chapter 3: Functions & Code Organization

## What is this chapter about?
This chapter explains functions, how to break code into smaller parts for easier maintenance and reuse, and how to pass and return values from functions.

**Example:**
If you want to write a function to add two numbers, such as add(2, 3) and get the result 5.

## Functions
Function declaration:
```go
func add(a int, b int) int {
    return a + b
}
```
Calling a function:
```go
sum := add(2, 3)
fmt.Println(sum)
```
Output:
```
5
```

Example of a function with no parameters:
```go
func hello() {
    fmt.Println("Hello!")
}
hello()
```
Output:
```
Hello!
```

## Multiple Return Values
```go
func swap(a, b string) (string, string) {
    return b, a
}
x, y := swap("hello", "world")
fmt.Println(x, y)
```
Output:
```
world hello
```

## Named Return Values
```go
func calc(x int) (result int) {
    result = x * 2
    return
}
fmt.Println(calc(5))
```
Output:
```
10
```

## Variadic Functions
```go
func sum(nums ...int) int {
    total := 0
    for _, n := range nums {
        total += n
    }
    return total
}
fmt.Println(sum(1, 2, 3, 4))
```
Output:
```
10
```

## Defer, Panic, Recover
```go
func main() {
    defer fmt.Println("End of program")
    fmt.Println("Start program")
}
```
Output:
```
Start program
End of program
```

## Variable Scope
Variables declared inside a function are only accessible within that function.
```go
func foo() {
    x := 10
    fmt.Println(x)
}
// fmt.Println(x) // error: x undefined
```

## Packages
Create a new file and use `package` + import.
```go
// In mathutil/math.go
package mathutil
func Double(x int) int { return x * 2 }

// In main.go
import "./mathutil"
fmt.Println(mathutil.Double(5))
```

[Go by Example: Functions](https://gobyexample.com/functions)
[Go by Example: Multiple Return Values](https://gobyexample.com/multiple-return-values)
[Go by Example: Variadic Functions](https://gobyexample.com/variadic-functions)
[Go by Example: Defer](https://gobyexample.com/defer)

---
