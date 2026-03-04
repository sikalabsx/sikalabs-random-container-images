FROM golang:1.25 AS builder-slu-master
RUN go install github.com/sikalabs/slu@master

FROM golang:1.25 AS builder-slr-master
WORKDIR /build
RUN go install github.com/sikalabs/slr@master

FROM debian:13-slim
COPY --from=builder-slu-master /go/bin/slu /usr/local/bin/slu
COPY --from=builder-slr-master /go/bin/slr /usr/local/bin/slr
