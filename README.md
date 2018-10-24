# Ubuntu
> Ubuntu Docker images.


## "Dev" Image

This image is based on the official "minimal" docker image from Canonical.
It comes with essential dev tools installed.
It includes language support for C/C++, Python, Node.js, C# (.Net Core), Go, Java, Scala, Kotlin, Swift, and Rust.
The `dev` image also comes with PostgreSQL and MongoDB installed (although they might need some configurations).

You can find pre-built images on https://hub.docker.com/r/tinylinux/ubuntu-18.04/

The name of the current dev image is `tinylinux/ubuntu-18.04:0.2.2-dev`.

<!--
docker build -f ./18.04-dev/Dockerfile -t tinylinux/ubuntu-18.04:0.2.2-dev .
docker run -it --rm -p 8000:80 -p 52022:22 -p 55432:5432 -p 57017:27017 --name ubuntu-18.04-dev <image_id>
docker push tinylinux/ubuntu-18.04:0.2.2-dev
docker run -it -p 8000:80 -p 52022:22 -p 55432:5432 -p 57017:27017 --name ubuntu-18.04-dev tinylinux/ubuntu-18.04:0.2.2-dev
-->

```bash
docker pull tinylinux/ubuntu-18.04:0.2.2-dev
docker run -it -p 8000:80 -p 52022:22 -p 55432:5432 -p 57017:27017 --name my-dev-ubuntu tinylinux/ubuntu-18.04:0.2.2-dev
```

The first thing you may want to do after starting a container is to add a (non-sudo) user.


You can also modify the Dockerfile to suit your needs, and build your own image:

```bash
docker build -f ./18.04-dev/Dockerfile .
docker run -it -p 8000:80 -p 52022:22 -p 55432:5432 -p 57017:27017 --name my-own-ubuntu <image_id>
```


<!--
** Configure postgresql:
su postgres
psql
\password
psql -h localhost -U postgres
-->

<!--
adduser user
-->


## "Dev-Workstation" Image (Experimental)

The "dev-workstation" image is built on top of the `dev` image.
The workstation image includes full ubuntu-desktop package 

You can find pre-built images on https://hub.docker.com/r/tinylinux/ubuntu-18.04/

The name of the current dev image is `tinylinux/ubuntu-18.04:0.2.2-dev-workstation`.

<!--
docker build -f ./18.04-dev-workstation/Dockerfile -t tinylinux/ubuntu-18.04:0.2.2-dev-workstation .
docker run -it --rm -p 8000:80 -p 52022:22 -p 5901:5901 -p 55432:5432 -p 57017:27017 --name ubuntu-18.04-workstation <image_id>
docker push tinylinux/ubuntu-18.04:0.2.2-dev-workstation
docker run -it -p 8000:80 -p 52022:22 -p 5901:5901 -p 55432:5432 -p 57017:27017 --name ubuntu-18.04-workstation tinylinux/ubuntu-18.04:0.2.2-dev-workstation
-->

```bash
docker pull tinylinux/ubuntu-18.04:0.2.2-dev-workstation
docker run -it -p 8000:80 -p 52022:22 -p 5901:5901 -p 55432:5432 -p 57017:27017 --name my-workstation-ubuntu tinylinux/ubuntu-18.04:0.2.2-dev-workstation
```


## How to Create Custom Image

Instead of creating a new image by modifying the Dockerfile,
you can customize a running container instance,
and then create a new image.


```bash
docker commit <container_id> <name>  
```


## What Packages are Included?

In order to see what packages are currently installed in these packages,
run the following command in the container:

```bash
apt list --installed
```

