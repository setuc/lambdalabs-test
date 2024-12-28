ARG BASE_IMAGE
ARG BASE_IMAGE_TAG
FROM ${BASE_IMAGE}:${BASE_IMAGE_TAG}

# Install python3-venv first
RUN apt-get update && apt-get install -y python3-venv

# Create ubuntu user
RUN useradd -m -s /bin/bash -u 1000 ubuntu

# Create workspace and set permissions
RUN mkdir -p /workspace && \
    chown -R ubuntu:ubuntu /workspace

# Switch to ubuntu user before installing uv
USER ubuntu
WORKDIR /workspace

# Install uv for ubuntu user
RUN curl -LsSf https://astral.sh/uv/install.sh | sh
ENV PATH="/home/ubuntu/.local/bin:/home/ubuntu/.cargo/bin:$PATH"

# Create and set permissions for virtual environment
ENV VIRTUAL_ENV=/workspace/venv
RUN python -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Install development tools using uv
RUN uv pip install \
    pytest \
    black \
    flake8 \
    ipykernel \
    jupyter
