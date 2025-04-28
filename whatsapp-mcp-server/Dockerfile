# Use a Python base image
FROM python:3.9-slim

# Set working directory
WORKDIR /app

# Install system dependencies (including ffmpeg for audio conversion)
RUN apt-get update && apt-get install -y --no-install-recommends \
    ffmpeg \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements first for better caching
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code
COPY . .

# Create necessary directories
RUN mkdir -p /app/whatsapp-bridge/store

# Expose port if needed (if the server listens on a port)
EXPOSE 8080

# Command to run the server
CMD ["python", "main.py"]