FROM python:3.11-slim

# Install system dependencies (e.g., for document processing if needed)
RUN apt-get update && apt-get install -y \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Copy requirements first to leverage Docker cache
COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application
COPY . .

# Expose the port the app runs on (Render uses PORT env var)
EXPOSE 8000

# Start the application
CMD uvicorn main:app --host 0.0.0.0 --port ${PORT:-8000}
