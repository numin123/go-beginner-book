# Chapter 9: Database Interaction
# What is this chapter about?
This chapter explains what a database is, how to store data, and how to connect to and manage data in a database, such as adding, deleting, updating, and searching.

**Example:**
If you want to store user information in your program, such as name, email, registration date, and quickly search for this data.
# What is a Database?

A database is a large, organized storage for data, like a notebook or a file cabinet, making it easy to find and use information, such as user lists, product lists, or order history.

Key things beginners should know about databases:
- Databases store large amounts of data in an organized way
- Data is usually stored in "tables"; each row is a record, each column is a detail (e.g., name, email, registration date)
- You can quickly add, delete, update, or search data in a database
- Popular databases: MySQL, PostgreSQL, SQLite, SQL Server
- You need to know basic commands: INSERT (add), SELECT (search), UPDATE (edit), DELETE (remove)

# Example table structure (users)

| id  | username | email             | created_at          |
|-----|----------|-------------------|---------------------|
| 1   | alice    | alice@email.com   | 2025-07-15 10:00:00 |
| 2   | bob      | bob@email.com     | 2025-07-15 10:05:00 |
| 3   | charlie  | charlie@email.com | 2025-07-15 10:10:00 |



## SQL Databases
Connect and use SQL databases
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
Output (example):
```
1 Ann
2 Bob
```

## Using ORM (Optional)
Example: GORM
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
Output (example):
```
[{1 Ann}]
```

[Go by Example: SQL](https://gobyexample.com/sql)
[GORM Docs](https://gorm.io/docs/)

---
