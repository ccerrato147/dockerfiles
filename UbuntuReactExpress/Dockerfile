# Image for web front end in docker

FROM ubuntu

# Setting environment variables to have a reference to the HOME directory and to specify it's a none interactive shell session
ENV HOME /root
ENV DEBIAN_FRONTEND noninteractive

# Replace shell with bash so we can source files
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# Update source list, install git, curl, screen (in case your in remote sessions) and emacs
RUN apt-get update -y && apt-get install -y git && apt-get install -y curl && apt-get install -y screen && apt-get install -y emacs24-nox emacs24-el emacs24-common-non-dfsg

# Setting more environment variables because we need to make reference to those values several times
ENV NVM_DIR /usr/local/nvm
ENV NODE_VERSION 0.12.2

# Install and load nvm, node and install jshint to allow checking of JS code within emacs and install gulp for task automation
# The last two commands are optional, jshint and gulp are not necessary to work with node.js
RUN curl https://raw.githubusercontent.com/creationix/nvm/v0.25.0/install.sh | bash && source $NVM_DIR/nvm.sh && nvm install $NODE_VERSION && nvm alias default $NODE_VERSION && nvm use default && npm install jshint -g && npm install gulp -g && npm install express -g && npm install nodemon -g

# Create Toji Directory (You can name it what ever you want), which is where we will set our code later
RUN cd $HOME && mkdir webapp

# Exposing port, this is the port I use for my app, change it to the one you use in your node app
# You can expose as many ports as you want
EXPOSE 3000