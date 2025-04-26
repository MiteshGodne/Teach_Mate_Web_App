FROM python:3.11-slim

# Install libssl and other required build tools
RUN apt-get update && apt-get install -y \
    libssl-dev \
    libffi-dev \
    gcc \
    && apt-get clean

# Set working directory
WORKDIR /app

# Copy code
COPY . .

# Install dependencies
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

# Expose the port uvicorn will run on
EXPOSE 8000

# Start the app
CMD ["sh", "-c", "uvicorn app.main:app --host 0.0.0.0 --port ${PORT:-8000}"]
