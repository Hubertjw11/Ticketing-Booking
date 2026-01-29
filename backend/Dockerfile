FROM golang:1.24-alpine

WORKDIR /src/app

RUN go install github.com/cosmtrek/air@v1.51.0

COPY . .

RUN go mod tidy