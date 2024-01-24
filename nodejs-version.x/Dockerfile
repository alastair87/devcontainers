FROM alastair87/debian:latest
LABEL maintainer="Alastair Cooper <alastair@alastair87.me>"
ARG NODE_MAJOR=20
ARG USER="user"
USER root
# RUN curl -fsSL https://deb.nodesource.com/setup_${VERSION}.x | bash - &&\
#     apt-get install -y nodejs && \
#     apt-get autoclean
RUN apt-get update && \
    apt-get install -y  ca-certificates gnupg && \
    apt-get autoclean
RUN mkdir -p /etc/apt/keyrings && \
    curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg && \
    echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list
RUN apt-get update && \
    apt-get install -y nodejs && \
    apt-get autoclean
USER ${USER}
RUN mkdir /home/${USER}/.npm-global/lib /home/${USER}/.npm-global/bin -p && \
    npm config set prefix /home/${USER}/.npm-global && \
    npm i -g npm@latest yarn@latest bun@latest && \
    echo export PATH=$HOME/.npm-global/bin:$PATH >> /home/${USER}/.zshrc
ENTRYPOINT ["tini", "-s", "--"]
CMD [ "/bin/zsh" ]
