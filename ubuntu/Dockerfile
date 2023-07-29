FROM docker.io/library/ubuntu:22.04
LABEL maintainer="Alastair Cooper <alastair@alastair87.me>"
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y zsh git bat exa fzf direnv curl wget sudo tini && \
    apt-get autoclean
RUN wget -O /tmp/starship.tar.gz https://github.com/starship/starship/releases/latest/download/starship-$(uname -m)-unknown-linux-musl.tar.gz && \
    tar xvf /tmp/starship.tar.gz -C /usr/local/bin && \
    rm /tmp/starship.tar.gz
COPY key-bindings.zsh /usr/share/doc/fzf/examples/key-bindings.zsh
ARG USER="user"
RUN adduser --shell /bin/zsh ${USER}
USER ${USER}
WORKDIR /home/${USER}
COPY --chown=${USER}:${USER} dot-zshrc /home/${USER}/.zshrc
COPY --chown=${USER}:${USER} starship.toml /home/${USER}/.config/
ADD --chown=${USER}:${USER} https://git.io/antigen /home/${USER}/.antigen/antigen.zsh
RUN zsh -c "source /home/${USER}/.zshrc"
ENTRYPOINT ["tini", "-s", "--"]
CMD [ "/bin/zsh" ]
