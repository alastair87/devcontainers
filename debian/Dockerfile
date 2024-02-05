FROM docker.io/library/debian:stable-slim
LABEL maintainer="Alastair Cooper <alastair@alastair87.me>"
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y zsh git bat exa fzf direnv curl wget sudo tini man vim-nox && \
    apt-get autoclean
RUN ln -s /usr/bin/batcat /usr/bin/bat && \
    ln -s /usr/bin/exa /usr/bin/eza
RUN wget -O /tmp/install.sh https://starship.rs/install.sh && \
    sh /tmp/install.sh -y && \
    rm /tmp/install.sh
COPY key-bindings.zsh /usr/share/doc/fzf/examples/key-bindings.zsh
ARG USER="user"
RUN adduser --shell /bin/zsh ${USER}
USER ${USER}
WORKDIR /home/${USER}
RUN echo "export EDITOR=/usr/bin/vim" >> /home/${USER}/.profile
COPY --chown=${USER}:${USER} dot-zshrc /home/${USER}/.zshrc
COPY --chown=${USER}:${USER} starship.toml /home/${USER}/.config/
RUN mkdir .antigen && \
    curl -L git.io/antigen > /home/${USER}/.antigen/antigen.zsh
RUN zsh -c "source /home/${USER}/.zshrc"
ENTRYPOINT ["tini", "-s", "--"]
CMD [ "/bin/zsh" ]
