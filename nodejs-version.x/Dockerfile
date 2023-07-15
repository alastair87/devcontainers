FROM docker.io/alastair87/ubuntu:latest
LABEL maintainer="Alastair Cooper <alastair@alastair87.me>"
ARG VERSION="lts"
ARG USER="user"
USER root
RUN curl -fsSL https://deb.nodesource.com/setup_${VERSION}.x | bash - &&\
    apt-get install -y nodejs && \
    apt-get autoclean
USER ${USER}
RUN mkdir /home/${USER}/.npm-global/lib /home/${USER}/.npm-global/bin -p && \
    npm config set prefix /home/${USER}/.npm-global && \
    npm i -g npm@latest yarn@latest && \
    echo export PATH=$HOME/.npm-global/bin:$PATH >> /home/${USER}/.zshrc
ENTRYPOINT ["tini", "-s", "--"]
CMD [ "/bin/zsh" ]
