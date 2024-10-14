FROM golang:1.19

# Set the working directory inside the container
WORKDIR /app

# Copy go.mod and go.sum first to leverage Docker cache
COPY go.mod go.sum ./

# Download all dependencies. This helps caching dependencies in Docker
RUN go mod download

# Copy the rest of the application code
COPY . .

# Expose port 8080
EXPOSE 8080

# Build the Go application
RUN go build -o backend .

# Run the Go application
CMD ["./backend"]