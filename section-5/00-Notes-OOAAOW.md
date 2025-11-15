# Install and Build Go for *src/product-catalog/README.md*
1. run the command:
   ```
   sudo apt install golang-go
   ```
2. check version of go
   ```
   go --version
   ```
3. clone the repo [https://github.com/abuabddullah/ultimate-devops-project-demo.git](https://github.com/abuabddullah/ultimate-devops-project-demo.git)
4. go to **src/product-catalog/README.md** folder of **ultimate-devops-project-demo** project
5. set the env
   ```
   export PRODUCT_CATALOG_PORT=8088
   ```
7. build the prject *[go.mod টাই হচ্ছে package.json এর মত কাজ করে]*
   ```
   go build -o product-catalog . 
   ```
8. terminal out put
```
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo/src/product-catalog$ ll
total 28748
drwxrwxr-x  4 ubuntu ubuntu     4096 Nov 15 01:01 ./
drwxrwxr-x 28 ubuntu ubuntu     4096 Nov 14 14:12 ../
-rw-rw-r--  1 ubuntu ubuntu      606 Nov 14 12:49 Dockerfile
-rw-rw-r--  1 ubuntu ubuntu      670 Nov 14 12:49 README.md
drwxrwxr-x  3 ubuntu ubuntu     4096 Nov 14 12:49 genproto/
-rw-rw-r--  1 ubuntu ubuntu     3815 Nov 14 12:49 go.mod
-rw-rw-r--  1 ubuntu ubuntu    21347 Nov 14 12:49 go.sum
-rw-rw-r--  1 ubuntu ubuntu     8741 Nov 14 12:49 main.go
drwxrwxr-x  2 ubuntu ubuntu     4096 Nov 14 12:49 products/
-rw-rw-r--  1 ubuntu ubuntu      518 Nov 14 12:49 tools.go
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo/src/product-catalog$ export PRODUCT_CATALOG_PORT=8088
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo/src/product-catalog$ go build -o product-catalog .
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo/src/product-catalog$ ll
total 28748
drwxrwxr-x  4 ubuntu ubuntu     4096 Nov 15 01:01 ./
drwxrwxr-x 28 ubuntu ubuntu     4096 Nov 14 14:12 ../
-rw-rw-r--  1 ubuntu ubuntu      606 Nov 14 12:49 Dockerfile
-rw-rw-r--  1 ubuntu ubuntu      670 Nov 14 12:49 README.md
drwxrwxr-x  3 ubuntu ubuntu     4096 Nov 14 12:49 genproto/
-rw-rw-r--  1 ubuntu ubuntu     3815 Nov 14 12:49 go.mod
-rw-rw-r--  1 ubuntu ubuntu    21347 Nov 14 12:49 go.sum
-rw-rw-r--  1 ubuntu ubuntu     8741 Nov 14 12:49 main.go
-rwxrwxr-x  1 ubuntu ubuntu 29366641 Nov 15 01:01 product-catalog*
drwxrwxr-x  2 ubuntu ubuntu     4096 Nov 14 12:49 products/
-rw-rw-r--  1 ubuntu ubuntu      518 Nov 14 12:49 tools.go
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo/src/product-catalog$ ./product-catalog 
INFO[0000] Loaded 10 products                           
INFO[0000] Product Catalog gRPC server started on port: 8088 

```

# Dockerize the go-project
1. create a **Dockerfile** at **src/product-catalog/Dockerfile**
```
FROM golang:1.22-alpine AS builder

WORKDIR /usr/src/app/

# Use Go build cache for dependencies
RUN --mount=type=cache,target=/go/pkg/mod \
    --mount=type=cache,target=/root/.cache/go-build \
    mkdir -p /root/.cache/go-build



# Copy
COPY go.mod go.sum ./

# Download
RUN go mod download

# Copy the rest of the source code
COPY . .

RUN go build -o /go/build/product-catalog ./

####################################

FROM alpine AS release

WORKDIR /usr/src/app/

COPY ./products/ ./products/
COPY --from=builder /go/build/product-catalog ./

# ENV PRODUCT_CATALOG_PORT=8088
EXPOSE ${PRODUCT_CATALOG_PORT}
ENTRYPOINT [ "./product-catalog" ]
```
2. build the image
   ```
   docker build -t abuabddullah/product-catalog:v1
   ```
