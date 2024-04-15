FROM golang:1.19-alpine AS builder

# Set the Current Working Directory inside the container
WORKDIR /app

# Copy go.mod dan go.sum ke direktori kerja di dalam container
COPY main.go .

# Download semua dependensi. Dependensi akan di-cache jika go.mod dan go.sum tidak berubah
ENV GOOS=windows GOARCH=amd64

# Build aplikasi Go
RUN go build -o main

FROM alpine:latest

WORKDIR /app

COPY --from=builder /app/main app/main

# Expose port 8080 untuk akses ke aplikasi HTTP
EXPOSE 8080


CMD ["/app/main"]