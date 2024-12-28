ARG BASE_IMAGE
ARG BASE_IMAGE_TAG
FROM ${BASE_IMAGE}:${BASE_IMAGE_TAG}

# Create a non-root user
RUN useradd -m -s /bin/bash -u 1000 ubuntu

# Set permissions for the workspace
RUN mkdir -p /workspace && chown ubuntu:ubuntu /workspace

# Switch to non-root user
USER ubuntu
WORKDIR /workspace
