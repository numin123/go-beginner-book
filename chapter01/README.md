# บทที่ 1: เตรียมความพร้อมและทำความเข้าใจพื้นฐาน (Getting Started & Fundamentals)

## บทนี้คืออะไร?
บทนี้จะแนะนำให้รู้จักภาษา Go ว่าคืออะไร เหมาะกับใคร และมีจุดเด่นอะไร พร้อมทั้งสอนวิธีติดตั้ง Go และสร้างโปรแกรมแรกแบบง่ายๆ เช่น Hello World เพื่อให้ผู้เริ่มต้นเข้าใจภาพรวมและเริ่มต้นใช้งานได้ทันที

**ตัวอย่าง:**
ถ้าคุณไม่เคยเขียนโปรแกรมมาก่อน บทนี้จะช่วยให้คุณติดตั้ง Go และเขียนโปรแกรมแรกได้สำเร็จ เช่น แสดงข้อความ "Hello, Go!" บนหน้าจอ

## ทำไมต้องเรียน Go?
Go (Golang) คือภาษาโปรแกรมที่ Google พัฒนา ใช้งานง่าย เร็ว เหมาะกับงานเบื้องหลัง เว็บเซิร์ฟเวอร์ และงานที่ต้องการประสิทธิภาพสูง
- เขียนง่าย อ่านง่าย
- Compile เร็ว
- มี Garbage Collection
- เหมาะกับงาน Concurrency (รันหลายอย่างพร้อมกัน)
- ใช้ในบริษัทใหญ่ เช่น Google, Uber, Dropbox

[อ่านเพิ่ม: Why Go? (ภาษาอังกฤษ)](https://go.dev/doc/why-go)

## การติดตั้ง Go
1. เข้าเว็บ [https://go.dev/dl/](https://go.dev/dl/)
2. เลือกเวอร์ชันที่ตรงกับระบบปฏิบัติการ (Windows, macOS, Linux)
3. ติดตั้งตามขั้นตอน
4. เปิด Terminal/Command Prompt พิมพ์ `go version` ถ้าเห็นเวอร์ชันแปลว่าติดตั้งสำเร็จ

[คู่มือการติดตั้ง Go ภาษาไทย](https://devahoy.com/posts/go-install/)


## โครงสร้างโปรเจกต์ Go เบื้องต้น
- ไฟล์หลักชื่อ `main.go`
- ใช้ package `main` และฟังก์ชัน `main()`
- ใช้ package `fmt` สำหรับแสดงผล

ตัวอย่าง Hello World:
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

ตัวอย่างรับค่าจากผู้ใช้และแสดงผล:
```go
package main
import "fmt"
func main() {
    var name string
    fmt.Print("ชื่อคุณ: ")
    fmt.Scan(&name)
    fmt.Println("สวัสดี", name)
}
```
Output:
```
ชื่อคุณ: John
สวัสดี John
```


## ไวยากรณ์พื้นฐาน
- ตัวแปร: `var x int = 10`
- ชนิดข้อมูล: int, float64, string, bool
- ค่าคงที่: `const pi = 3.14`

ตัวอย่าง:
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


## การดำเนินการ (Operators)
- +, -, *, /, % (คณิตศาสตร์)
- ==, !=, >, <, >=, <= (เปรียบเทียบ)
- &&, ||, ! (ตรรกะ)
- =, +=, -= (กำหนดค่า)

ตัวอย่าง:
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


## การรับและแสดงผล (Input/Output)
- แสดงผล: `fmt.Println("ข้อความ")`
- รับค่า: ดูตัวอย่างด้านบน

ตัวอย่างแสดงผลแบบจัดรูปแบบ:
```go
score := 95.5
fmt.Printf("คะแนน: %.1f\n", score)
```
Output:
```
คะแนน: 95.5
```


[Go by Example: Input/Output](https://gobyexample.com/hello-world)

---

## LeetCode ที่แนะนำสำหรับบทนี้
- [1108. Defanging an IP Address](https://leetcode.com/problems/defanging-an-ip-address/) (string, basic output)
- [771. Jewels and Stones](https://leetcode.com/problems/jewels-and-stones/) (string, count)
- [1672. Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/) (array, for loop)
