# build stage
FROM golang:1.21 as builder

WORKDIR /app
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o go-app .

# runtime stage
FROM alpine:latest

WORKDIR /app
COPY --from=builder /app/go-app .
EXPOSE 8080
CMD [ "./go-app" ]