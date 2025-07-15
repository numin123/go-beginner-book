# บทที่ 5: พอยน์เตอร์และอินเทอร์เฟซ (Pointers & Interfaces)


## พอยน์เตอร์ (Pointers)
ชี้ไปที่ตำแหน่งในหน่วยความจำ
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
Nil Pointer คือ pointer ที่ยังไม่ชี้ไปไหน


## เมธอด (Methods)
ฟังก์ชันที่ผูกกับ struct
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


## อินเทอร์เฟซ (Interfaces)
กำหนดรูปแบบเมธอดที่ struct ต้องมี
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


## Empty Interface (interface{}) และ Type Assertion
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

## LeetCode ที่แนะนำสำหรับบทนี้
- [160. Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/) (pointer)
- [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) (pointer, struct)
- [876. Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/) (pointer)
