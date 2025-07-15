# Chapter 8: Networking

## What is this chapter about?
This chapter teaches you how to write programs that connect to the internet or a network, such as sending data via HTTP or creating a simple web server.

**Example:**
If you want your program to fetch data from a website or create a small web server that responds with "Hello, world!" when someone visits.

## HTTP Clients
Send HTTP GET/POST
```go
import (
    "net/http"
    "io/ioutil"
    "fmt"
)
resp, _ := http.Get("https://example.com")
body, _ := ioutil.ReadAll(resp.Body)
fmt.Println(string(body[:50])) // Show only first 50 chars
resp.Body.Close()
```
Output:
```
<!doctype html><html>... (example output)
```

## HTTP Servers
Create a simple web server
```go
import (
    "net/http"
)
http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
    w.Write([]byte("Hello, world!"))
})
http.ListenAndServe(":8080", nil)
```
Output (when opening http://localhost:8080):
```
Hello, world!
```

## RESTful APIs
Concept: Receive/send JSON data via HTTP
Example handler for POST JSON:
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
