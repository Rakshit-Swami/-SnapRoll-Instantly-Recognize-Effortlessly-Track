# Use an official Python runtime as a parent image
FROM python:3.8-slim-buster

# Set the working directory in the container
WORKDIR /app

# Install required system dependencies
RUN apt-get update -y && apt-get install -y \
    ffmpeg libsm6 libxext6 \
    cmake libboost-all-dev \
    build-essential

# Copy the project files into the container
COPY . /app

# Upgrade pip
RUN pip install --upgrade pip

# Install project dependencies
RUN pip install -r requirements.txt

# Install Gmail APIs for email alerts
RUN pip install --upgrade google-api-python-client google-auth-httplib2 google-auth-oauthlib

# Expose the Flask application port
EXPOSE 5000

# Command to run the application
CMD ["python", "-m", "flask", "--app", "src/app.py", "run", "--host=0.0.0.0"]
