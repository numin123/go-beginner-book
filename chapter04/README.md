# บทที่ 4: โครงสร้างข้อมูล (Data Structures)

## บทนี้คืออะไร?
บทนี้จะสอนเรื่องการเก็บข้อมูลหลายๆ ค่า เช่น อาร์เรย์ (array) และสไลซ์ (slice) เพื่อให้จัดการข้อมูลจำนวนมากได้ง่ายขึ้น

**ตัวอย่าง:**
ถ้าคุณอยากเก็บคะแนนสอบของนักเรียนหลายคนไว้ในตัวแปรเดียว แล้วนำไปวนลูปแสดงผลทีละคน


## อาร์เรย์ (Arrays)
เก็บข้อมูลขนาดคงที่
```go
var nums [3]int = [3]int{1, 2, 3}
fmt.Println(nums[0])
for i := 0; i < len(nums); i++ {
    fmt.Println(nums[i])
}
```
Output:
```
1
1
2
3
```


## สไลซ์ (Slices)
ขนาดยืดหยุ่น เพิ่ม/ลดได้
```go
nums := []int{1, 2, 3}
nums = append(nums, 4)
fmt.Println(nums)
for _, v := range nums {
    fmt.Println(v)
}
```
Output:
```
[1 2 3 4]
1
2
3
4
```


## make, copy
```go
s := make([]int, 3)
copy(s, nums)
fmt.Println(s)
```
Output:
```
[1 2 3]
```


## แผนที่ (Maps)
เก็บข้อมูลแบบ key-value
```go
m := map[string]int{"a": 1, "b": 2}
fmt.Println(m["a"])
for k, v := range m {
    fmt.Println(k, v)
}
```
Output:
```
1
a 1
b 2
```


## โครงสร้าง (Structs)
สร้างชนิดข้อมูลเอง
```go
type Person struct {
    Name string
    Age  int
}
p := Person{"Ann", 20}
fmt.Println(p.Name, p.Age)
```
Output:
```
Ann 20
```

d := Dog{Animal{"Doggy"}, "Pug"}

## การฝัง (Embedding) ใน Structs
```go
type Animal struct { Name string }
type Dog struct {
    Animal
    Breed string
}
d := Dog{Animal{"Doggy"}, "Pug"}
fmt.Println(d.Name, d.Breed)
```
Output:
```
Doggy Pug
```


[Go by Example: Arrays](https://gobyexample.com/arrays)
[Go by Example: Slices](https://gobyexample.com/slices)
[Go by Example: Maps](https://gobyexample.com/maps)
[Go by Example: Structs](https://gobyexample.com/structs)

---

## LeetCode ที่แนะนำสำหรับบทนี้
- [1. Two Sum](https://leetcode.com/problems/two-sum/) (array, map)
- [88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/) (array, slice)
- [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) (array, map)
