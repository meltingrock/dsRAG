FROM python:3.12

WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    git \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements file
COPY ../requirements.txt .

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy source code
COPY .. .

# Install the package in development mode
RUN pip install -e .

# Install huggingface
RUN pip install transformers torch sentence-transformers

# Set environment variables
ENV PYTHONPATH=/app

# Create directory for data storage
RUN mkdir -p /app/data

# Command to run when the container starts
CMD ["python", "-c", "import dsrag; print('dsRAG is ready!')"]
