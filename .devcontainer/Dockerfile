# Use a minimal Ubuntu base image (slim)
FROM ubuntu:22.04 as base

# Set environment variables to avoid user interaction during package installations
ENV DEBIAN_FRONTEND=noninteractive

# Install Dart, Python, and essential utilities
RUN apt-get update && apt-get install -y --no-install-recommends \
    apt-transport-https \
    ca-certificates \
    curl \
    wget \
    python3 \
    python3-pip \
    software-properties-common && \
    # Install Dart
    wget -qO- https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - && \
    sh -c 'wget -qO- https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list' && \
    apt-get update && apt-get install -y --no-install-recommends dart && \
    # Install Jupyter
    pip3 install --no-cache-dir notebook jupyterlab && \
    # Clean up unnecessary files and reduce image size
    apt-get remove --purge -y software-properties-common apt-transport-https && \
    apt-get autoremove -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Set default python and dart commands to be executable from any shell session
RUN ln -s /usr/bin/python3 /usr/bin/python && ln -s /usr/bin/dart /usr/local/bin/dart

# Verify installation
RUN python --version && pip --version && dart --version
