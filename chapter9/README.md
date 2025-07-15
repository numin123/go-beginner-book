# บทที่ 9: การจัดการฐานข้อมูล (Database Interaction)


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

## LeetCode ที่แนะนำสำหรับบทนี้
- [175. Combine Two Tables](https://leetcode.com/problems/combine-two-tables/) (SQL)
- [595. Big Countries](https://leetcode.com/problems/big-countries/) (SQL)
- [183. Customers Who Never Order](https://leetcode.com/problems/customers-who-never-order/) (SQL)
