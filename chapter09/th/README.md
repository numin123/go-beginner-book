# บทที่ 9: การจัดการฐานข้อมูล (Database Interaction)
# บทนี้คืออะไร?
บทนี้จะอธิบายว่าดาต้าเบสคืออะไร ใช้เก็บข้อมูลอย่างไร และสอนวิธีเชื่อมต่อและจัดการข้อมูลในฐานข้อมูล เช่น การเพิ่ม ลบ แก้ไข ค้นหา

**ตัวอย่าง:**
ถ้าคุณอยากเก็บข้อมูลผู้ใช้ในโปรแกรม เช่น ชื่อ อีเมล วันสมัคร และค้นหาข้อมูลเหล่านี้ได้อย่างรวดเร็ว
# ดาต้าเบส (Database) คืออะไร?

ดาต้าเบส คือ ที่เก็บข้อมูลขนาดใหญ่ที่มีการจัดระเบียบอย่างเป็นระบบ เช่น ตารางข้อมูล เหมือนสมุดจดหรือแฟ้มเอกสารที่ใช้เก็บข้อมูลต่าง ๆ ให้ค้นหาและนำมาใช้ได้ง่าย เช่น รายชื่อผู้ใช้ รายการสินค้า หรือประวัติการสั่งซื้อ

สิ่งสำคัญที่ควรรู้เกี่ยวกับดาต้าเบสสำหรับผู้เริ่มต้น:
- ดาต้าเบสใช้เก็บข้อมูลจำนวนมากให้เป็นระเบียบ
- ข้อมูลในดาต้าเบสมักถูกจัดเก็บในรูปแบบ "ตาราง" (Table) โดยแต่ละแถวคือข้อมูล 1 รายการ แต่ละคอลัมน์คือรายละเอียดแต่ละอย่าง เช่น ชื่อ, อีเมล, วันสมัคร
- เราสามารถเพิ่ม ลบ แก้ไข หรือค้นหาข้อมูลในดาต้าเบสได้อย่างรวดเร็ว
- ดาต้าเบสที่นิยม เช่น MySQL, PostgreSQL, SQLite, SQL Server
- การใช้งานดาต้าเบสต้องรู้จักคำสั่งพื้นฐาน เช่น การเพิ่มข้อมูล (INSERT), ค้นหา (SELECT), แก้ไข (UPDATE), และลบ (DELETE)

# ตัวอย่างโครงสร้างตาราง (users)

| id  | username | email             | created_at          |
|-----|----------|-------------------|---------------------|
| 1   | alice    | alice@email.com   | 2025-07-15 10:00:00 |
| 2   | bob      | bob@email.com     | 2025-07-15 10:05:00 |
| 3   | charlie  | charlie@email.com | 2025-07-15 10:10:00 |



## SQL Databases
เชื่อมต่อและใช้งานฐานข้อมูล SQL
```go
import (
    "database/sql"
    _ "github.com/lib/pq" // PostgreSQL driver
    "fmt"
)
db, err := sql.Open("postgres", "user=postgres dbname=test sslmode=disable")
if err != nil {
    fmt.Println("connect error:", err)
    return
}
rows, err := db.Query("SELECT id, name FROM users")
for rows.Next() {
    var id int
    var name string
    rows.Scan(&id, &name)
    fmt.Println(id, name)
}
```
Output (ตัวอย่าง):
```
1 Ann
2 Bob
```

## การใช้ ORM (Optional)
เช่น GORM
```go
import (
    "gorm.io/gorm"
    "gorm.io/driver/sqlite"
    "fmt"
)
db, _ := gorm.Open(sqlite.Open("test.db"), &gorm.Config{})
type User struct { ID int; Name string }
db.Create(&User{Name: "Ann"})
var users []User
db.Find(&users)
fmt.Println(users)
```
Output (ตัวอย่าง):
```
[{1 Ann}]
```

[Go by Example: SQL](https://gobyexample.com/sql)
[GORM Docs](https://gorm.io/docs/)

---
