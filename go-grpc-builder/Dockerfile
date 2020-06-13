FROM golang:1.14-alpine

RUN apk update && apk add --no-cache git gcc libc-dev

RUN go get -u google.golang.org/grpc
RUN go get -u google.golang.org/protobuf/...

RUN go get -u github.com/grpc-ecosystem/go-grpc-middleware

CMD ["/bin/ash"]
