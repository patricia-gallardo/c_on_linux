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

RUN mkdir /var/run/sshd

# Set password to conlinux
RUN echo 'root:conlinux' | chpasswd

RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN sed -i 's/UsePAM yes/#UsePAM yes/' /etc/ssh/sshd_config

ENV NOTVISIBLE "in users profile"

RUN echo "export VISIBLE=now" >> /etc/profile

# Declare the port number the container should expose
EXPOSE 2222

CMD ["/usr/sbin/sshd", "-D"]

# HOW TO TEST:
# docker build -t toolchain .
# docker run -d -p 2222:22 --name test_toolchain toolchain
# (docker port test_toolchain)
# ssh root@localhost -p 2222
# Password is the one you set above (colinux)

# HOW TO CLEAN UP:
# docker container stop test_toolchain
# docker container rm test_toolchain
