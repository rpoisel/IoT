FROM golang:1.15 as builder
WORKDIR /go/src/IoT
COPY . .
WORKDIR /go/src/IoT/cmd/loxone-proxy
RUN go build -o loxone-proxy


FROM debian:bullseye-slim
WORKDIR /
COPY --from=builder /go/src/IoT/cmd/loxone-proxy/loxone-proxy .
RUN apt-get update && apt-get install -yy ca-certificates

CMD ["/loxone-proxy"]

