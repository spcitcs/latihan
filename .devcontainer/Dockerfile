# Use an Ubuntu base image
FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install Dart
RUN sudo apt-get update && \
    sudo apt-get install -y apt-transport-https && \
    wget -qO- https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - && \
    sudo sh -c 'wget -qO- https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list' && \
    sudo apt-get update && \
    sudo apt-get install -y dart

# Install Python
RUN sudo apt-get install -y python3 python3-pip
