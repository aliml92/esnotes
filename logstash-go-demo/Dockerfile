FROM golang:latest

COPY go.mod go.sum /go/src/github.com/aliml92/esnotes/logstash-go-demo/
WORKDIR /go/src/github.com/aliml92/esnotes/logstash-go-demo/
RUN go mod download
COPY . /go/src/github.com/aliml92/esnotes/logstash-go-demo
RUN go build -o /usr/bin/logstash-go-demo github.com/aliml92/esnotes/logstash-go-demo/cmd/api

EXPOSE 8080 8080
ENTRYPOINT ["/usr/bin/logstash-go-demo"]