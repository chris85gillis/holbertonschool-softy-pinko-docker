# Use the latest Ubuntu as the base image
FROM ubuntu:latest

# Update APT package lists
RUN apt-get update

# Upgrade currently installed packages
RUN apt-get upgrade -y

# Install Python 3 and pip3
RUN apt-get install -y python3 python3-pip

# Install Flask
RUN pip3 install flask

# Set the working directory to /app
WORKDIR /app
COPY api.py /app/api.py

CMD ["python3", "/app/api.py"]
