FROM golang:1.17-alpine as builder

RUN apk add --no-cache git

# fetch code and move to the directory
RUN git clone https://github.com/jandelgado/gcov2lcov.git
WORKDIR gcov2lcov

# Cache PD dependencies
RUN GO111MODULE=on go mod download

# Replace orig main with the modified main.
COPY ./main.go ./

RUN ls

RUN go build -o /gcov2lcov

# Move the instrumented binary to a dedicated container
FROM alpine

COPY --from=builder /gcov2lcov /

ENTRYPOINT ["/gcov2lcov"]

