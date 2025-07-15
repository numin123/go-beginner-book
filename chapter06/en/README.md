# Chapter 6: Concurrency

## What is this chapter about?
This chapter teaches how to run multiple tasks at the same time in a single program, such as using goroutines and channels to make your program faster and more responsive.

**Example:**
If you want your program to load data from the internet and process it at the same time, without waiting for each step to finish.

## Goroutines
Run lightweight functions concurrently
```go
import (
    "fmt"
    "time"
)
go func() {
    fmt.Println("Hello from goroutine")
}()
fmt.Println("Main thread")
time.Sleep(time.Second)
```
Output:
```
Main thread
Hello from goroutine
```

## Channels
Send data between goroutines
```go
ch := make(chan int)
go func() { ch <- 1 }()
x := <-ch
fmt.Println(x)
```
Output:
```
1
```

## Select Statement
Choose the ready channel
```go
ch1 := make(chan string)
ch2 := make(chan string)
go func() { ch1 <- "one" }()
go func() { ch2 <- "two" }()
select {
case msg := <-ch1:
    fmt.Println(msg)
case msg := <-ch2:
    fmt.Println(msg)
}
```
Output (could be one or two):
```
one
```

## Mutexes
Lock data to prevent simultaneous modification
```go
import "sync"
var mu sync.Mutex
count := 0
mu.Lock()
count++
mu.Unlock()
fmt.Println(count)
```
Output:
```
1
```

## WaitGroup
Wait for goroutines to finish
```go
import (
    "fmt"
    "sync"
)
var wg sync.WaitGroup
wg.Add(2)
go func() {
    defer wg.Done()
    fmt.Println("goroutine 1 done")
}()
go func() {
    defer wg.Done()
    fmt.Println("goroutine 2 done")
}()
wg.Wait()
```
Output:
```
goroutine 1 done
goroutine 2 done
```

[Go by Example: Goroutines](https://gobyexample.com/goroutines)
[Go by Example: Channels](https://gobyexample.com/channels)
[Go by Example: Select](https://gobyexample.com/select)
[Go by Example: Mutexes](https://gobyexample.com/mutexes)
[Go by Example: WaitGroups](https://gobyexample.com/waitgroups)

---
