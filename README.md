# Ubuntu
> Ubuntu Docker images.


## "Dev" image

This image is based on the official "minimal" docker image from Canonical.
It comes with essential dev tools installed.
It includes language support for C/C++, Python, Node.js, C# (.Net Core), Go, Java, Scala, Kotlin, Swift, and Rust.

You can find pre-built images on https://hub.docker.com/r/tinylinux/ubuntu-18.04/

The name of the current dev image is `tinylinux/ubuntu-18.04:0.1.1-dev`.

<!--
docker build -f ./18.04-dev/Dockerfile -t tinylinux/ubuntu-18.04:0.1.1-dev .
docker run -it --name ubuntu-18.04-dev <image_id>
docker push tinylinux/ubuntu-18.04:0.1.1-dev
docker run -it --name ubuntu-18.04-dev tinylinux/ubuntu-18.04:0.1.1-dev
-->

```bash
docker pull tinylinux/ubuntu-18.04:0.1.0-dev
docker run -it --name my-dev-ubuntu tinylinux/ubuntu-18.04:0.1.0-dev
```


You can also modify the Dockerfile to suit your needs, and build your own image:

```bash
docker build -f ./18.04-dev/Dockerfile .
docker run -it --name my-own-ubuntu <image_id>
```

