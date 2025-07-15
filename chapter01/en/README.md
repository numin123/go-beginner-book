# Chapter 1: Getting Started & Fundamentals

## What is this chapter about?
This chapter introduces the Go programming language, who it is for, and its key features. It also guides you through installing Go and creating your first simple program, such as Hello World, so beginners can quickly understand the basics and get started.

**Example:**
If you have never programmed before, this chapter will help you install Go and write your first program, such as displaying "Hello, Go!" on the screen.

## Why learn Go?
Go (Golang) is a programming language developed by Google. It is easy to use, fast, and suitable for backend, web servers, and high-performance tasks.
- Easy to write and read
- Fast compilation
- Has garbage collection
- Great for concurrency (running many things at once)
- Used by big companies like Google, Uber, Dropbox

[Read more: Why Go?](https://go.dev/doc/why-go)

## Installing Go
1. Visit [https://go.dev/dl/](https://go.dev/dl/)
2. Choose the version for your operating system (Windows, macOS, Linux)
3. Follow the installation steps
4. Open Terminal/Command Prompt and type `go version`. If you see the version, installation is successful.

[Go installation guide (Thai)](https://devahoy.com/posts/go-install/)

## Basic Go Project Structure
- Main file is `main.go`
- Use `package main` and the `main()` function
- Use the `fmt` package for output

Hello World example:
```go
package main
import "fmt"
func main() {
    fmt.Println("Hello, Go!")
}
```
Output:
```
Hello, Go!
```

Example: Input from user and output:
```go
package main
import "fmt"
func main() {
    var name string
    fmt.Print("Your name: ")
    fmt.Scan(&name)
    fmt.Println("Hello", name)
}
```
Output:
```
Your name: John
Hello John
```

## Basic Syntax
- Variable: `var x int = 10`
- Data types: int, float64, string, bool
- Constant: `const pi = 3.14`

Example:
```go
var age int = 20
var name string = "Ann"
const pi = 3.14
fmt.Println(age, name, pi)
```
Output:
```
20 Ann 3.14
```

## Operators
- +, -, *, /, % (arithmetic)
- ==, !=, >, <, >=, <= (comparison)
- &&, ||, ! (logical)
- =, +=, -= (assignment)

Example:
```go
a := 5
b := 2
fmt.Println(a + b) // 7
fmt.Println(a > b) // true
fmt.Println(a == 5 && b == 2) // true
```
Output:
```
7
true
true
```

## Input/Output
- Output: `fmt.Println("text")`
- Input: see example above

Formatted output example:
```go
score := 95.5
fmt.Printf("Score: %.1f\n", score)
```
Output:
```
Score: 95.5
```

[Go by Example: Input/Output](https://gobyexample.com/hello-world)

---
