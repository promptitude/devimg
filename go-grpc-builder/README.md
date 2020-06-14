Go gRPC builder
================

base image for building gRPC microservice

usage
------

```Dockerfile
FROM docker.pkg.github.com/promptitude/devimg/go-grpc-builder:latest AS builder

WORKDIR $GOPATH/src/github.com/promptitude/sample-grpc

COPY ./pb ./pb
COPY ./service ./service
COPY main.go ./

RUN go test && go build -o svc && mv ./svc /usr/local/bin/

FROM alpine:3.11

WORKDIR /usr/local/bin

COPY --from=builder /usr/local/bin/svc /usr/local/bin/svc

EXPOSE 12345

CMD ["/bin/ash", "-c", "/usr/local/bin/svc"]
```
