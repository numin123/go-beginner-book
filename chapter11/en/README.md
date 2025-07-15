# Chapter 11: Project Development & Deployment

## What is this chapter about?
This chapter explains how to manage large projects, use Go Modules, and deploy your program, such as building a Docker image.

**Example:**
If you want to split your code into multiple files and folders, or deploy your program to a real server.

## Managing Dependencies (Go Modules)
```go
go mod init myproject
go get github.com/some/package
```
Output:
```
go: creating new go.mod: module myproject
go: added github.com/some/package v1.2.3
```

## Structuring Large Projects
- Separate folders by feature, e.g., /user, /order
- Use main.go as the entrypoint
Example:
```
myproject/
  main.go
  user/
    handler.go
  order/
    handler.go
```

## Building a Docker Image
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

## Deploying Go Applications
- Use Docker, Kubernetes, or Cloud (GCP, AWS, Azure)
Example deploy on Kubernetes:
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
