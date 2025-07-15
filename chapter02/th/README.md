# บทที่ 2: การควบคุมการทำงานของโปรแกรม (Control Flow)

## บทนี้คืออะไร?
บทนี้จะสอนเรื่องการควบคุมทิศทางของโปรแกรม เช่น การตัดสินใจ (if-else, switch) เพื่อให้โปรแกรมตอบสนองต่อเงื่อนไขต่างๆ ได้

**ตัวอย่าง:**
ถ้าคุณอยากให้โปรแกรมแสดงข้อความต่างกันตามอายุผู้ใช้ เช่น ถ้าอายุเกิน 18 ให้แสดง "บรรลุนิติภาวะ" ถ้าน้อยกว่านั้นให้แสดง "ยังไม่บรรลุนิติภาวะ"

## เงื่อนไข (Conditional Statements)
Go ใช้ if, else if, else และ switch

ตัวอย่าง if-else:
```go
age := 18
if age >= 18 {
    fmt.Println("บรรลุนิติภาวะ")
} else {
    fmt.Println("ยังไม่บรรลุนิติภาวะ")
}
```
Output:
```
บรรลุนิติภาวะ
```

ตัวอย่าง if-else-if:
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

ตัวอย่าง switch:
```go
score := 80
switch {
case score >= 80:
    fmt.Println("เกรด A")
case score >= 70:
    fmt.Println("เกรด B")
default:
    fmt.Println("เกรด C หรือต่ำกว่า")
}
```
Output:
```
เกรด A
```

## การวนซ้ำ (Loops)
Go มีแค่ for loop แต่ใช้ได้หลายแบบ

ตัวอย่าง for:
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

for แบบ while:
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

## การจัดการข้อผิดพลาดเบื้องต้น (Basic Error Handling)

Go คืนค่า error เสมอถ้าเกิดปัญหา
```go
result, err := someFunc()
if err != nil {
    fmt.Println("เกิดข้อผิดพลาด:", err)
} else {
    fmt.Println("ผลลัพธ์:", result)
}
```
Output (ถ้า error):
```
เกิดข้อผิดพลาด: some error
```

[Go by Example: If/Else](https://gobyexample.com/if-else)
[Go by Example: For](https://gobyexample.com/for)
[Go by Example: Switch](https://gobyexample.com/switch)
[Go by Example: Errors](https://gobyexample.com/errors)

---
