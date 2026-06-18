FROM ubuntu:24.04

# Python バージョン (uv が管理)
ARG PYTHON_VERSION=3.13
ARG USERNAME=vscode

ENV PYTHON_VERSION=${PYTHON_VERSION}
ENV DEBIAN_FRONTEND=noninteractive
ENV LANG=C.UTF-8

# uv のインストール先を共通の場所に固定
ENV UV_INSTALL_DIR=/usr/local/bin
# uv が管理する Python をシステム全体で共有
ENV UV_PYTHON_INSTALL_DIR=/opt/uv/python

# 基本パッケージと uv のインストール
RUN apt-get update \
    && apt-get install -y \
        curl \
        ca-certificates \
        gnupg \
        git \
        jq \
        tmux \
    && useradd -m -s /bin/bash $USERNAME \
    && curl -LsSf https://astral.sh/uv/install.sh | sh \
    && mkdir -p $UV_PYTHON_INSTALL_DIR \
    && uv python install $PYTHON_VERSION \
    && chmod -R a+rX $UV_PYTHON_INSTALL_DIR \
    && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL https://gist.githubusercontent.com/DIO0550/1830ced050035c34668aa426f7258346/raw/install-gh.sh | bash

USER $USERNAME

SHELL ["/bin/bash", "-l", "-c"]
RUN curl -fsSL https://gist.githubusercontent.com/DIO0550/148b1392cf435ba3562da0d398bee442/raw/install-ai-tools.sh | bash
RUN curl -fsSL https://gist.githubusercontent.com/DIO0550/356434ec2b182f71d99dc0c467555ba5/raw/tmux-setup.sh | bash

WORKDIR /workspace
