FROM docker.io/alastair87/debian:latest
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs > rustup.sh && \
    chmod +x rustup.sh && \
    ./rustup.sh -y && \
    rm rustup.sh && \
    echo source $HOME/.cargo/env >> $HOME/.zshrc