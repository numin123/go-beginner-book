# บทที่ 6: การทำงานพร้อมกัน (Concurrency)


## Goroutines
รันฟังก์ชันพร้อมกันแบบเบาๆ
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

x := <-ch

## Channels
ส่งข้อมูลระหว่าง goroutine
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
เลือก channel ที่พร้อมใช้งาน
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
Output (อาจได้ one หรือ two):
```
one
```


## Mutexes
ล็อกข้อมูลไม่ให้แก้พร้อมกัน
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
รอให้ goroutine ทำงานเสร็จ
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

## LeetCode ที่แนะนำสำหรับบทนี้
- [1114. Print in Order](https://leetcode.com/problems/print-in-order/) (goroutine, sync)
- [1195. Fizz Buzz Multithreaded](https://leetcode.com/problems/fizz-buzz-multithreaded/) (goroutine, channel)
- [1226. The Dining Philosophers](https://leetcode.com/problems/the-dining-philosophers/) (mutex)
