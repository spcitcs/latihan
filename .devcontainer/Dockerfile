# Use an Ubuntu base image
FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install Dart
RUN sudo apt-get update && \
    sudo apt-get install -y apt-transport-https wget && \
    wget -qO- https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - && \
    sudo sh -c 'wget -qO- https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list' && \
    sudo apt-get update && \
    sudo apt-get install -y dart

# Install Python
RUN sudo apt-get install -y python3 python3-pip

# Install Jupyter
RUN pip3 install notebook jupyterlab

# Install additional dependencies (if needed for live share, etc.)
RUN sudo apt-get install -y git curl

# Clean up
RUN sudo apt-get clean && \
    sudo rm -rf /var/lib/apt/lists/*
