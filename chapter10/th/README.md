# บทที่ 10: การทดสอบและการดีบัก (Testing & Debugging)

## บทนี้คืออะไร?
บทนี้จะสอนวิธีตรวจสอบความถูกต้องของโปรแกรมด้วยการเขียนเทสต์ (test) และวิธีแก้ไขข้อผิดพลาด (debug) เพื่อให้โปรแกรมทำงานถูกต้อง

**ตัวอย่าง:**
ถ้าคุณอยากรู้ว่าโค้ดที่เขียนทำงานถูกต้องหรือไม่ หรืออยากหาจุดผิดพลาดในโปรแกรม

## การเขียน Unit Tests
ใช้ package `testing`
```go
import "testing"
func add(a, b int) int { return a + b }
func TestAdd(t *testing.T) {
    got := add(2, 3)
    if got != 5 {
        t.Errorf("want 5 got %d", got)
    }
}
```
Output (เมื่อรัน `go test`):
```
PASS
```

## การเขียน Benchmark Tests
```go
func BenchmarkAdd(b *testing.B) {
    for i := 0; i < b.N; i++ {
        add(2, 3)
    }
}
```
Output (เมื่อรัน `go test -bench .`):
```
BenchmarkAdd-8   1000000000   0.25 ns/op
```

## การดีบัก
ใช้ Delve (dlv)
- ติดตั้ง: `go install github.com/go-delve/delve/cmd/dlv@latest`
- ใช้: `dlv debug`
ตัวอย่างการตั้ง breakpoint:
```
dlv debug
(dlv) break main.go:5
(dlv) continue
```

[Go by Example: Testing](https://gobyexample.com/testing-and-benchmarking)
[Delve Debugger](https://github.com/go-delve/delve)

---
