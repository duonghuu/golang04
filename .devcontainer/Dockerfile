FROM golang:1.25

# Tạo user vscode
RUN groupadd --gid 1000 vscode \
    && useradd --uid 1000 --gid vscode --shell /bin/bash --create-home vscode

# Cài đặt công cụ
RUN apt-get update && apt-get install -y \
    git \
    curl \
    vim \
    && rm -rf /var/lib/apt/lists/*

# Cài đặt Go tools
RUN go install golang.org/x/tools/gopls@latest
RUN go install github.com/go-delve/delve/cmd/dlv@latest

# Set working directory
WORKDIR /workspace

# Chuyển ownership cho vscode user
RUN chown -R vscode:vscode /workspace

USER vscode