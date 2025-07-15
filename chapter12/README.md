# บทที่ 12: หัวข้อขั้นสูง (Advanced Topics)


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
จัดการ timeout/cancel ใน goroutine
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
ตรวจสอบ/แก้ไขชนิดข้อมูลขณะรันไทม์
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
ใช้ `go generate` หรือเครื่องมือเช่น stringer
ตัวอย่าง stringer: [https://pkg.go.dev/golang.org/x/tools/cmd/stringer](https://pkg.go.dev/golang.org/x/tools/cmd/stringer)


[Go Generics](https://go.dev/doc/go1.18#generics)
[Go by Example: Context](https://gobyexample.com/context)
[Go by Example: Reflection](https://gobyexample.com/reflect)
[Go Generate](https://blog.golang.org/generate)

---

## LeetCode ที่แนะนำสำหรับบทนี้
- [128. Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/) (map, advanced)
- [42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/) (slice, advanced)
- [295. Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/) (struct, heap)
