# Chapter 7: File Handling & I/O

## What is this chapter about?
This chapter explains how to read and write files, such as saving data to a file or reading data from a file, including basic I/O operations.

**Example:**
If you want your program to save text to a file or read a text file and display its contents on the screen.

## Reading and Writing Files
```go
import (
    "os"
    "fmt"
)
file, err := os.Create("test.txt")
if err != nil {
    fmt.Println("error:", err)
    return
}
file.WriteString("hello world\n")
file.Close()

file, err = os.Open("test.txt")
buf := make([]byte, 20)
n, _ := file.Read(buf)
fmt.Println(string(buf[:n]))
file.Close()
```
Output:
```
hello world
```

## Buffered I/O
```go
import (
    "bufio"
    "os"
    "fmt"
)
file, _ := os.Open("test.txt")
reader := bufio.NewReader(file)
line, _ := reader.ReadString('\n')
fmt.Println(line)
file.Close()
```
Output:
```
hello world
```

## Working with CSV/JSON/XML
```go
import (
    "encoding/csv"
    "encoding/json"
    "os"
    "fmt"
)
// CSV
csvWriter := csv.NewWriter(os.Stdout)
csvWriter.Write([]string{"a", "b"})
csvWriter.Flush()
// JSON
b, _ := json.Marshal(map[string]int{"a": 1})
fmt.Println(string(b))
```
Output:
```
a,b
{"a":1}
```

[Go by Example: Reading Files](https://gobyexample.com/reading-files)
[Go by Example: Writing Files](https://gobyexample.com/writing-files)
[Go by Example: JSON](https://gobyexample.com/json)

---
