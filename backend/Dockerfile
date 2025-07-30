# Use a lightweight base image with Python 3.10
FROM python:3.10-slim

# Install dependencies for dlib and face recognition
RUN apt-get update && apt-get install -y \
    build-essential \
    cmake \
    git \
    curl \
    libgtk-3-dev \
    libboost-all-dev \
    libssl-dev \
    libffi-dev \
    libpq-dev \
    libatlas-base-dev \
    libgl1-mesa-glx \
    libglib2.0-0 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Create app directory
WORKDIR /app

# Copy requirements
COPY requirements.txt .

# Install pip dependencies
RUN pip install --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt

# Copy your entire project
COPY . .

# Expose the port FastAPI will run on
EXPOSE 8000

# Command to run your app (change if your entrypoint is different)
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
