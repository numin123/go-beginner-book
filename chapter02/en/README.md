# Chapter 2: Control Flow

## What is this chapter about?
This chapter teaches you how to control the flow of your program, such as making decisions (if-else, switch), so your program can respond to different conditions.

**Example:**
If you want your program to display different messages based on the user's age, e.g., if age is over 18, show "Adult"; otherwise, show "Not adult yet".

## Conditional Statements
Go uses if, else if, else, and switch.

Example if-else:
```go
age := 18
if age >= 18 {
    fmt.Println("Adult")
} else {
    fmt.Println("Not adult yet")
}
```
Output:
```
Adult
```

Example if-else-if:
```go
score := 75
if score >= 80 {
    fmt.Println("A")
} else if score >= 70 {
    fmt.Println("B")
} else {
    fmt.Println("C")
}
```
Output:
```
B
```

Example switch:
```go
score := 80
switch {
case score >= 80:
    fmt.Println("Grade A")
case score >= 70:
    fmt.Println("Grade B")
default:
    fmt.Println("Grade C or below")
}
```
Output:
```
Grade A
```

## Loops
Go only has for loop, but it can be used in many ways.

Example for:
```go
for i := 1; i <= 5; i++ {
    fmt.Println(i)
}
```
Output:
```
1
2
3
4
5
```

While-style for:
```go
n := 1
for n < 5 {
    fmt.Println(n)
    n++
}
```
Output:
```
1
2
3
4
```

## Basic Error Handling
Go always returns an error value if something goes wrong.
```go
result, err := someFunc()
if err != nil {
    fmt.Println("Error:", err)
} else {
    fmt.Println("Result:", result)
}
```
Output (if error):
```
Error: some error
```

[Go by Example: If/Else](https://gobyexample.com/if-else)
[Go by Example: For](https://gobyexample.com/for)
[Go by Example: Switch](https://gobyexample.com/switch)
[Go by Example: Errors](https://gobyexample.com/errors)

---
