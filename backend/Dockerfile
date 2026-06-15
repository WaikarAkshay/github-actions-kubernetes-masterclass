FROM golang:1.26-alpine AS builder

WORKDIR /app

COPY . .

RUN go mod tidy && CGO_ENABLED=0 GOOS=linux go build -o skillpulse .

FROM alpine:3.23

WORKDIR /app

COPY --from=builder /app/skillpulse .

EXPOSE 8080 

CMD ["./skillpulse"]