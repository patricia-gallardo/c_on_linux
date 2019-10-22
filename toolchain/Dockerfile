FROM ubuntu:18.04

RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get install -y cmake
RUN apt-get install -y gcc
RUN apt-get install -y clang
RUN apt-get install -y gdb
RUN apt-get install -y build-essential
RUN apt-get install -y openssh-server
RUN apt-get install -y rsync

# Get conan
RUN apt-get update
RUN apt-get install -y python3-pip
RUN pip3 install conan

RUN mkdir /var/run/sshd

# Set password to conlinux
RUN echo 'root:conlinux' | chpasswd

RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN sed -i 's/UsePAM yes/#UsePAM yes/' /etc/ssh/sshd_config

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
