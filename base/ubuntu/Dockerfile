ARG UBUNTU_VERSION="24.04"
FROM docker.io/library/ubuntu:${UBUNTU_VERSION}
LABEL maintainer="Alastair Cooper <alastair@alastair87.me>"
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y zsh git bat eza fzf direnv curl wget sudo tini && \
    curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg && \
    chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | tee /etc/apt/sources.list.d/github-cli.list > /dev/null && \
    apt-get update && \
    apt-get install -y gh && \
    apt-get autoclean && \
    rm -rf /var/lib/apt/lists/*
RUN wget -O /tmp/install.sh https://starship.rs/install.sh && \
    sh /tmp/install.sh -y && \
    rm /tmp/install.sh
COPY shared/shell/key-bindings.zsh /usr/share/doc/fzf/examples/key-bindings.zsh
ARG USER="ubuntu"
# RUN adduser --shell /bin/zsh --uid 1000 ${USER}
USER ${USER}
WORKDIR /home/${USER}
COPY --chown=${USER}:${USER} shared/shell/dot-zshrc /home/${USER}/.zshrc
COPY --chown=${USER}:${USER} shared/shell/starship.toml /home/${USER}/.config/
ADD --chown=${USER}:${USER} https://git.io/antigen /home/${USER}/.antigen/antigen.zsh
RUN zsh -c "source /home/${USER}/.zshrc"
ENTRYPOINT ["tini", "-s", "--"]
CMD [ "/bin/zsh" ]
