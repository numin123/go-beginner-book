# Chapter 5: Pointers & Interfaces

## What is this chapter about?
This chapter explains pointers, which are used to reference memory locations, and interfaces, which help you write flexible and reusable code.

**Example:**
If you want to change the value of a variable from another function, or want different structs to work together using an interface.

## Pointers
Reference memory locations
```go
x := 10
p := &x
fmt.Println(*p) // 10
*p = 20
fmt.Println(x) // 20
```
Output:
```
10
20
```
Nil Pointer is a pointer that doesn't point anywhere yet.

## Methods
Functions attached to structs
```go
type Person struct {
    Name string
}
func (p Person) SayHi() {
    fmt.Println("Hi!", p.Name)
}
p := Person{"Ann"}
p.SayHi()
```
Output:
```
Hi! Ann
```

## Interfaces
Define method sets that structs must have
```go
type Speaker interface {
    SayHi()
}
type Person struct{ Name string }
func (p Person) SayHi() { fmt.Println("Hi!", p.Name) }
func greet(s Speaker) { s.SayHi() }
p := Person{"Ann"}
greet(p)
```
Output:
```
Hi! Ann
```

## Empty Interface (interface{}) and Type Assertion
```go
var i interface{} = "hello"
s := i.(string)
fmt.Println(s)
```
Output:
```
hello
```

[Go by Example: Pointers](https://gobyexample.com/pointers)
[Go by Example: Methods](https://gobyexample.com/methods)
[Go by Example: Interfaces](https://gobyexample.com/interfaces)

---
