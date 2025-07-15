# บทที่ 11: การพัฒนาโปรเจกต์และการนำไปใช้งานจริง (Project Development & Deployment)


## การจัดการ Dependencies (Go Modules)
```go
go mod init myproject
go get github.com/some/package
```
Output:
```
go: creating new go.mod: module myproject
go: added github.com/some/package v1.2.3
```


## การจัดโครงสร้างโปรเจกต์ขนาดใหญ่
- แยกโฟลเดอร์ตามฟีเจอร์ เช่น /user, /order
- ใช้ main.go สำหรับ entrypoint
ตัวอย่าง:
```
myproject/
  main.go
  user/
    handler.go
  order/
    handler.go
```


## การสร้าง Docker Image
```dockerfile
FROM golang:1.22
WORKDIR /app
COPY . .
RUN go build -o app
CMD ["./app"]
```
Output:
```
Successfully built <image-id>
```


## การนำ Go Application ขึ้น Deployment
- ใช้ Docker, Kubernetes, หรือ Cloud (GCP, AWS, Azure)
ตัวอย่าง deploy บน Kubernetes:
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: go-app
spec:
  replicas: 2
  template:
    spec:
      containers:
      - name: go-app
        image: myrepo/go-app:latest
        ports:
        - containerPort: 8080
```


[Go Modules](https://blog.golang.org/using-go-modules)
[Deploy Go with Docker](https://docs.docker.com/language/golang/build-images/)

---

## LeetCode ที่แนะนำสำหรับบทนี้
- [70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) (function, structuring code)
- [198. House Robber](https://leetcode.com/problems/house-robber/) (function, module)
- [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) (function)
