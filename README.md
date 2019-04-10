# OpenJDK / Maven / Sencha Cmd docker image

Inspired by [rockmagicnet](https://github.com/rockmagic)'s work for Sencha Cmd. See [DockerHub](https://hub.docker.com/r/rockmagicnet/sencha-cmd) or [Github](https://github.com/rockmagic/sencha-cmd).

One can pull this image using:
* version 7-3.6.0-3.0.2

  ```docker pull cvagner/docker-jdk-maven-sencha-cmd:7-3.6.0-3.0.2```

## Using image for automated builds

Execute one of the following commands:

```bash
# Sencha CMD
docker run --rm -v `pwd`:/app -w /app \
  cvagner/docker-jdk-maven-sencha-cmd:7-3.6.0-3.0.2 \
  sencha

# Java
docker run --rm -v `pwd`:/app -w /app \
  cvagner/docker-jdk-maven-sencha-cmd:7-3.6.0-3.0.2 \
  java -version

# Maven
docker run --rm -v `pwd`:/app -w /app \
  cvagner/docker-jdk-maven-sencha-cmd:7-3.6.0-3.0.2 \
  mvn -v
```

Note that the absolute path is provided with `pwd` command. For Sencha Cmd instructions please refer the official documentation at https://docs.sencha.com/cmd/

## Building / publishing an image

Example:

```bash
VERSION_TAG=7-3.6.0-3.0.2
docker login
cd ${VERSION_TAG}
docker build --tag=cvagner/docker-jdk-maven-sencha-cmd:${VERSION_TAG} .
docker push cvagner/docker-jdk-maven-sencha-cmd:${VERSION_TAG}
```
