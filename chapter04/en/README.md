# Chapter 4: Data Structures

## What is this chapter about?
This chapter teaches you how to store multiple values, such as using arrays and slices, so you can manage large amounts of data more easily.

**Example:**
If you want to store exam scores for many students in a single variable and loop through them to display each score.

## Arrays
Fixed-size data storage
```go
var nums [3]int = [3]int{1, 2, 3}
fmt.Println(nums[0])
for i := 0; i < len(nums); i++ {
    fmt.Println(nums[i])
}
```
Output:
```
1
1
2
3
```

## Slices
Flexible size, can add/remove
```go
nums := []int{1, 2, 3}
nums = append(nums, 4)
fmt.Println(nums)
for _, v := range nums {
    fmt.Println(v)
}
```
Output:
```
[1 2 3 4]
1
2
3
4
```

## make, copy
```go
s := make([]int, 3)
copy(s, nums)
fmt.Println(s)
```
Output:
```
[1 2 3]
```

## Maps
Key-value data storage
```go
m := map[string]int{"a": 1, "b": 2}
fmt.Println(m["a"])
for k, v := range m {
    fmt.Println(k, v)
}
```
Output:
```
1
a 1
b 2
```

## Structs
Create your own data types
```go
type Person struct {
    Name string
    Age  int
}
p := Person{"Ann", 20}
fmt.Println(p.Name, p.Age)
```
Output:
```
Ann 20
```

## Embedding in Structs
```go
type Animal struct { Name string }
type Dog struct {
    Animal
    Breed string
}
d := Dog{Animal{"Doggy"}, "Pug"}
fmt.Println(d.Name, d.Breed)
```
Output:
```
Doggy Pug
```

[Go by Example: Arrays](https://gobyexample.com/arrays)
[Go by Example: Slices](https://gobyexample.com/slices)
[Go by Example: Maps](https://gobyexample.com/maps)
[Go by Example: Structs](https://gobyexample.com/structs)

---
