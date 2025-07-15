# บทที่ 7: การจัดการไฟล์และ I/O (File Handling & I/O)

## บทนี้คืออะไร?
บทนี้จะอธิบายวิธีอ่านและเขียนไฟล์ เช่น การบันทึกข้อมูลลงไฟล์หรืออ่านข้อมูลจากไฟล์ รวมถึงการใช้งาน I/O เบื้องต้น

**ตัวอย่าง:**
ถ้าคุณอยากให้โปรแกรมบันทึกข้อความลงไฟล์ หรืออ่านไฟล์ข้อความมาแสดงผลบนหน้าจอ

## การอ่านและเขียนไฟล์ (Reading and Writing Files)
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

## บัฟเฟอร์ I/O (Buffered I/O)
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

## การทำงานกับ CSV/JSON/XML
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
