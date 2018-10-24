# Custom Ubuntu desktop version for developers.
# It includes IDE tools and it runs VNC server for desktop access.
FROM tinylinux/ubuntu-18.04:0.2.2-dev
LABEL imageName="Ubuntu Desktop workstation (amd64) for dev"
LABEL copyright="Copyright 2018 Harry Y"

ENV DEBIAN_FRONTEND noninteractive

RUN apt update && apt upgrade -y
RUN apt install -y ubuntu-desktop gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal
RUN apt install -y libgconf-2-4

RUN apt install -y firefox firefox-dev
RUN apt install -y vlc imagemagick graphicsmagick gimp inkscape ghostscript blender

# Install VS Code
RUN wget -q -O vscode.deb https://go.microsoft.com/fwlink/?LinkID=760868
RUN dpkg -i vscode.deb && rm vscode.deb

# Install IntelliJ
RUN wget -q -O intellij.tgz https://download.jetbrains.com/idea/ideaIC-2018.2.5.tar.gz
RUN tar -C /opt -xzf intellij.tgz && rm intellij.tgz
ENV PATH /opt/idea-IC-182.4892.20/bin:$PATH

# Install Eclipse
RUN wget -q -O eclipse.tgz http://mirrors.xmission.com/eclipse/technology/epp/downloads/release/2018-09/R/eclipse-java-2018-09-linux-gtk-x86_64.tar.gz
RUN tar -C /opt -xzf eclipse.tgz && rm eclipse.tgz
ENV PATH /opt/eclipse:$PATH

ENV DISPLAY :0

# Install VNC server
# RUN apt install -y tightvncserver
RUN apt install -y vnc4server

# TBD: Configure VNC server
# RUN vncserver :1

EXPOSE 5901
