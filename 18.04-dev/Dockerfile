# Custom Ubuntu desktop version for developers.
# Based on the official "minimal" image from Canonical.
FROM ubuntu:18.04
LABEL imageName="Ubuntu Desktop (amd64) for dev"
LABEL copyright="Copyright 2018 Harry Y"

ENV DEBIAN_FRONTEND noninteractive

RUN apt update && apt upgrade -y
# RUN apt install -y ubuntu-desktop
RUN apt install -y --no-install-recommends ubuntu-desktop 

# Base package for dev.
RUN apt install -y build-essential
RUN apt install -y cmake clang libicu-dev pkg-config
RUN apt install -y openssh-server

# You can comment out anything you don't need.
RUN apt install -y git nodejs npm curl wget xclip jq
RUN apt install -y emacs vim

# The system should already have python/python3 at this point.
RUN apt install -y python-pip python3-pip

# Install .Net SDK
RUN wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb && rm packages-microsoft-prod.deb
RUN apt install -y apt-transport-https && apt update
RUN apt install -y dotnet-sdk-2.1

# Install Go
RUN wget -q -O go.tgz https://dl.google.com/go/go1.11.1.linux-amd64.tar.gz
RUN tar -C /usr/local -xzf go.tgz && rm go.tgz
RUN mkdir -p /opt/go
ENV GOPATH /opt/go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH
RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"

# Install OpenJDK.
RUN apt install -y default-jdk
# Or, install Oracle JDK. 
# (Oracle JDK cannot be installed in non-interactive mode.)
# RUN apt install -y dialog apt-utils
# RUN add-apt-repository -y ppa:linuxuprising/java
# RUN DEBIAN_FRONTEND=dialog apt install -y oracle-java11-installer

# Install Maven
RUN wget -q -O maven.tgz http://mirrors.gigenet.com/apache/maven/maven-3/3.5.4/binaries/apache-maven-3.5.4-bin.tar.gz
RUN tar -C /opt -xzf maven.tgz && rm maven.tgz
ENV MAVEN_HOME /opt/apache-maven-3.5.4
ENV PATH $MAVEN_HOME/bin:$PATH

# Install Gradle
RUN wget -q -O gradle.zip https://services.gradle.org/distributions/gradle-4.10.2-bin.zip
RUN unzip gradle.zip -d /opt && rm gradle.zip
ENV GRADLE_HOME /opt/gradle-4.10.2
ENV PATH $GRADLE_HOME/bin:$PATH

# Install Scala
RUN echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823
RUN apt update && apt install -y sbt

# Install Kotlin
RUN wget -q -O kotlin.zip https://github.com/JetBrains/kotlin/releases/download/v1.2.71/kotlin-compiler-1.2.71-linux-x64.zip
RUN unzip kotlin.zip -d /opt && rm kotlin.zip
ENV PATH /opt/kotlinc/bin:$PATH

# Install Swift
RUN wget -q -O swift.tgz https://swift.org/builds/swift-4.2-release/ubuntu1804/swift-4.2-RELEASE/swift-4.2-RELEASE-ubuntu18.04.tar.gz
RUN tar -C /opt -xzf swift.tgz && rm swift.tgz
ENV PATH /opt/swift-4.2-RELEASE-ubuntu18.04/usr/bin:$PATH

# Install Rust
RUN mkdir -p /opt/rust
ENV RUSTUP_HOME /opt/rust
ENV CARGO_HOME /opt/rust
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y --no-modify-path
RUN . /opt/rust/env

# Install Typescript and other popular node lib/tools
RUN npm i -g npm@latest
RUN npm i -g typescript
RUN npm i -g @angular/cli create-react-app express-generator


# Install SQLite
RUN apt install -y sqlite3

# Install Redis
RUN apt install -y redis redis-tools
# RUN redis-server -v &

# Install PosgresQL
RUN apt install -y postgresql
RUN service postgresql start

# Install MongoDB
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4
RUN echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-4.0.list
RUN apt update && apt install -y mongodb-org
RUN mkdir -p /data/db
# RUN mongod &

# Install AWS SDK
RUN apt install -y awscli
# RUN aws configure

# Install Google Cloud SDK
RUN echo "deb http://packages.cloud.google.com/apt cloud-sdk-bionic main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
RUN curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
RUN apt update && apt install -y google-cloud-sdk
# RUN gcloud init


# Install VPN
RUN apt install -y network-manager-openconnect-gnome

# TBD: Create a user
# adduser user

EXPOSE 22 80 5432 27017
