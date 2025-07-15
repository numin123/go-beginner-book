# บทที่ 8: การทำงานกับเครือข่าย (Networking)

## บทนี้คืออะไร?
บทนี้จะสอนวิธีเขียนโปรแกรมที่เชื่อมต่อกับอินเทอร์เน็ตหรือเครือข่าย เช่น การส่งข้อมูลผ่าน HTTP หรือสร้างเว็บเซิร์ฟเวอร์ง่ายๆ

**ตัวอย่าง:**
ถ้าคุณอยากให้โปรแกรมดึงข้อมูลจากเว็บไซต์ หรือสร้างเว็บเซิร์ฟเวอร์เล็กๆ ที่ตอบข้อความ "Hello, world!" เมื่อมีคนเข้ามา


## HTTP Clients
ส่ง HTTP GET/POST
```go
import (
    "net/http"
    "io/ioutil"
    "fmt"
)
resp, _ := http.Get("https://example.com")
body, _ := ioutil.ReadAll(resp.Body)
fmt.Println(string(body[:50])) // แสดงแค่ 50 ตัวแรก
resp.Body.Close()
```
Output:
```
<!doctype html><html>... (ตัวอย่าง output)
```


## HTTP Servers
สร้างเว็บเซิร์ฟเวอร์ง่ายๆ
```go
import (
    "net/http"
)
http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
    w.Write([]byte("Hello, world!"))
})
http.ListenAndServe(":8080", nil)
```
Output (เมื่อเปิด http://localhost:8080):
```
Hello, world!
```


## RESTful APIs
แนวคิด: รับ/ส่งข้อมูลแบบ JSON ผ่าน HTTP
ตัวอย่าง handler รับ POST JSON:
```go
import (
    "encoding/json"
    "net/http"
)
type User struct { Name string }
http.HandleFunc("/user", func(w http.ResponseWriter, r *http.Request) {
    var u User
    json.NewDecoder(r.Body).Decode(&u)
    w.Write([]byte("Hello " + u.Name))
})
```


[Go by Example: HTTP Client](https://gobyexample.com/http-client)
[Go by Example: HTTP Server](https://gobyexample.com/http-server)

---

## LeetCode ที่แนะนำสำหรับบทนี้
- [771. Jewels and Stones](https://leetcode.com/problems/jewels-and-stones/) (string, input/output)
- [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) (stack, string)
- [387. First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/) (map, string)
