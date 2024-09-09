# Use a minimal Ubuntu base image (slim)
FROM ubuntu:22.04 as base

# Set environment variables to avoid user interaction during package installations
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    apt-transport-https \
    ca-certificates \
    curl \
    wget \
    python3 \
    python3-pip \
    software-properties-common
    
# Install Dart
RUN wget -qO- https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - && \
    sudo sh -c 'wget -qO- https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list' && \
    sudo apt-get update && \
    sudo apt-get install -y dart

# Install Python
RUN pip3 install --no-cache-dir notebook jupyterlab

# Clear Image
RUN apt-get remove --purge -y software-properties-common apt-transport-https && \
    apt-get autoremove -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Set default python and dart commands to be executable from any shell session
RUN ln -s /usr/bin/python3 /usr/bin/python && ln -s /usr/bin/dart /usr/local/bin/dart

# Verify installation
RUN python --version && pip --version && dart --version
