FROM golang:1.26-bookworm

RUN apt update && apt install -y \
    git \
    make \
    jq \
    curl \
    build-essential \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY app/ ./

ARG NODE_VERSION=local
ARG NODE_COMMIT=unknown
RUN make build VERSION="$NODE_VERSION" COMMIT="$NODE_COMMIT" BRANCH=local

RUN sed -i 's/\r$//' local-node.sh && \
    chmod +x local-node.sh

EXPOSE 26656 26657 1317 9090 8545 8546
