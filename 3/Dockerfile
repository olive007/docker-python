FROM python:3

MAINTAINER SECRET Olivier (olivier@devolive.be)

ARG GIT_URL=https://raw.githubusercontent.com/olive007/docker-commonFile

# Update the package list and
# Update packages to last version and
# Install several usefull packages
RUN DEBIAN_FRONTEND=noninteractive apt-get update && \
	DEBIAN_FRONTEND=noninteractive apt-get upgrade -y -qq && \
	DEBIAN_FRONTEND=noninteractive apt-get install -y -qq --no-install-recommends \
										locales \
										bash-completion \
										iproute2 \
										openssh-server \
										sudo \
										emacs-nox \
										openssl \
										wget \
										htop \
										curl \
										ca-certificates \
										unzip

# Replace the bash configuration
ADD $GIT_URL/master/etc/bash.bashrc /etc/bash.bashrc
RUN chmod 644 /etc/bash.bashrc

# Create the script directory
RUN mkdir -p /usr/local/script

# Copy the entry-point script
ADD $GIT_URL/master/usr/local/script/entry-point.sh /usr/local/script/entry-point.sh
RUN chmod 755 /usr/local/script/entry-point.sh

# Create the entry-point children directory
RUN mkdir /usr/local/script/entry-point.d/

# Copy the python script
ADD $GIT_URL/master/usr/local/script/entry-point.d/python.sh /usr/local/script/entry-point.d/python.sh

# Copy the startup script
ADD $GIT_URL/master/usr/local/script/startup.sh /usr/local/script/startup.sh
RUN chmod 755 /usr/local/script/startup.sh

# Copy the container-stopped script
ADD $GIT_URL/master/usr/local/script/startup.sh /usr/local/script/container-stopped.sh
RUN chmod 755 /usr/local/script/container-stopped.sh

# Define environment variables
ENV CONTAINER_LOCALE=en_US.UTF-8
ENV CONTAINER_USER_NAME=olive
ENV CONTAINER_USER_PASSWORD=test
ENV CONTAINER_USER_UID=1000
ENV CONTAINER_USER_GID=1000
ENV CONTAINER_URL_SSH_KEY=https://gist.githubusercontent.com/olive007/0eea691d672d827823877c180c4cc354/raw/docker_rsa.pub
ENV CONTAINER_URL_BASH_ALIASES=https://gist.githubusercontent.com/olive007/87f72fa69a071dc7d64430317b31d1f2/raw/bash.aliases
ENV CONTAINER_URL_BASH_PROMPT=https://gist.githubusercontent.com/olive007/87f72fa69a071dc7d64430317b31d1f2/raw/bash.prompt

ENTRYPOINT ["/usr/local/script/entry-point.sh"]

# By default launch the startup script and login as the user
CMD ["default-command"]
