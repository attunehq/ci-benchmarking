# x86_64 Ubuntu on an ARM Mac
FROM ubuntu:24.04

# Install necessary packages to build hurry
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        ca-certificates \
        wget \
        curl \
        build-essential \
        git && \
    rm -rf /var/lib/apt/lists/*

# Install Go
ARG GO_VERSION=1.25.4
ARG GO_ARCH=amd64

RUN wget https://go.dev/dl/go${GO_VERSION}.linux-${GO_ARCH}.tar.gz && \
    rm -rf /usr/local/go && \
    tar -C /usr/local -xzf go${GO_VERSION}.linux-${GO_ARCH}.tar.gz && \
    rm go${GO_VERSION}.linux-${GO_ARCH}.tar.gz

# Install Rust
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | \
    sh -s -- -y --default-toolchain stable

# Set PATH for Go and Cargo
ENV PATH="/usr/local/go/bin:/root/.cargo/bin:${PATH}"

# Set workspace
WORKDIR /workspace

CMD ["bash"]