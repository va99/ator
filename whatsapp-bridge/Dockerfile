FROM golang:1.24-alpine

WORKDIR /app

# Install required system dependencies
RUN apk add --no-cache gcc musl-dev sqlite-dev

# Copy go.mod and go.sum first to leverage Docker cache
COPY go.mod go.sum ./
RUN go mod download

# Copy the rest of the application
COPY . .

# Build the application
RUN go build -o whatsapp-bridge .

# Create directory for SQLite databases
RUN mkdir -p /data/store

# Expose the REST API port
EXPOSE 8080

# Set the volume for persistent data
VOLUME ["/data/store"]

# Run the application
CMD ["./whatsapp-bridge"]