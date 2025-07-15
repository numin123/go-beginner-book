# บทที่ 3: ฟังก์ชันและการจัดระเบียบโค้ด (Functions & Code Organization)

## บทนี้คืออะไร?
บทนี้จะอธิบายเรื่องฟังก์ชัน การแบ่งโค้ดเป็นส่วนย่อยๆ เพื่อให้แก้ไขและนำกลับมาใช้ซ้ำได้ง่ายขึ้น รวมถึงการรับค่าและส่งค่ากลับจากฟังก์ชัน

**ตัวอย่าง:**
ถ้าคุณอยากเขียนฟังก์ชันบวกเลขสองจำนวน เช่น add(2, 3) แล้วได้ผลลัพธ์ 5

## ฟังก์ชัน (Functions)
ประกาศฟังก์ชัน:
```go
func add(a int, b int) int {
    return a + b
}
```
เรียกใช้:
```go
sum := add(2, 3)
fmt.Println(sum)
```
Output:
```
5
```

ตัวอย่างฟังก์ชันไม่มีพารามิเตอร์:
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
    defer fmt.Println("จบโปรแกรม")
    fmt.Println("เริ่มโปรแกรม")
}
```
Output:
```
เริ่มโปรแกรม
จบโปรแกรม
```

## ขอบเขตของตัวแปร (Variable Scope)
ตัวแปรที่ประกาศในฟังก์ชันจะใช้ได้แค่ในฟังก์ชันนั้น
```go
func foo() {
    x := 10
    fmt.Println(x)
}
// fmt.Println(x) // error: x undefined
```

## แพ็คเกจ (Packages)
สร้างไฟล์ใหม่และใช้ `package` + import ได้เลย
```go
// ในไฟล์ mathutil/math.go
package mathutil
func Double(x int) int { return x * 2 }

// ในไฟล์ main.go
import "./mathutil"
fmt.Println(mathutil.Double(5))
```

[Go by Example: Functions](https://gobyexample.com/functions)
[Go by Example: Multiple Return Values](https://gobyexample.com/multiple-return-values)
[Go by Example: Variadic Functions](https://gobyexample.com/variadic-functions)
[Go by Example: Defer](https://gobyexample.com/defer)

---
