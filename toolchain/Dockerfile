FROM ubuntu:18.04

RUN echo "Updating repositories and installing required tools" \
    && export DEBIAN_FRONTEND="noninteractive" \
    && apt-get update \
    && apt-get -y dist-upgrade \
    && apt-get -y install \
       cmake \
       gcc \
       clang \
       gdb \
       build-essential \
       openssh-server \
       rsync \
    && echo "Cleaning system" \
    && apt-get autoclean \
    && apt-get clean \
    && apt-get autoremove --purge \
    && rm -rf /var/apt/cache/* \
    && rm -rf /tmp/*
       
RUN echo "Setting sshd configuration" \
    && mkdir -p /var/run/sshd \
    # Set password to conlinux
    && echo 'root:conlinux' | chpasswd \
    && sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config \
    && sed -i 's/UsePAM yes/#UsePAM yes/' /etc/ssh/sshd_config

# Declare the port number the container should expose
EXPOSE 2222

CMD ["/usr/sbin/sshd", "-D"]

# PREPARATION
# 1. (Mac) Install Docker Desktop for Mac (This probably requires a docker hub account)
#    https://hub.docker.com/editions/community/docker-ce-desktop-mac
# 2. Install CLion from Jetbrains
#    https://www.jetbrains.com/clion/download/

# MAC GIT NOTES
# Install xcode - Apple Store
# sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
# (Commandline tools) sudo xcode-select --install

# HOW TO TEST:
# docker build -t toolchain .
# docker run -d -p 2222:22 --name test_toolchain toolchain
# (docker port test_toolchain)
# ssh root@localhost -p 2222
# Password is the one you set above (conlinux)

# HOW TO CLEAN UP:
# docker container stop test_toolchain
# docker container rm test_toolchain
