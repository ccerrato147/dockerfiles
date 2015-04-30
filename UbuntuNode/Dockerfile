# Image for web front end in docker

FROM ubuntu

ENV HOME /root
ENV DEBIAN_FRONTEND noninteractive

# Replace shell with bash so we can source files
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

RUN apt-get update -y && apt-get install -y git && apt-get install -y curl && apt-get install -y screen && apt-get install -y emacs24-nox emacs24-el emacs24-common-non-dfsg

ENV NVM_DIR /usr/local/nvm
ENV NODE_VERSION 0.12.2

# Load nvm and install latest production node and install jshint to allow checking of JS code within emacs
RUN curl https://raw.githubusercontent.com/creationix/nvm/v0.25.0/install.sh | bash && source $NVM_DIR/nvm.sh && nvm install $NODE_VERSION && nvm alias default $NODE_VERSION && nvm use default && npm install -g jshint && npm install -g gulp

# Create Toji Directory
RUN cd $HOME && mkdir toji

# git pull and install dotfiles as well
RUN git clone https://github.com/ccerrato147/dotfiles.git
RUN ln -sb dotfiles/.screenrc .
RUN ln -sb dotfiles/.bash_profile .
RUN ln -sb dotfiles/.bashrc .
RUN ln -sb dotfiles/.bashrc_custom .
RUN ln -sf dotfiles/.emacs.d .

# Exposing port
EXPOSE 8087