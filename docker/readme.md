# Docker Container for Swashbucklin' Data Science

Currently the image contains the following tools:

- RStudio 4.4.1

The image also contains the following R packages (among many standard ones):

- rmarkdown
- tidyverse
- devtools
- workflowr
- BiocManager

It is easy to add packages from RStudio Server in the container, preserved for future use in the same container as long as it's not removed.

This image is based on Dave Tang's work highlighted in his blog post [Running RStudio Server with Docker](https://davetang.org/muse/2021/04/24/running-rstudio-server-with-docker/).

## Prerequisites

- Docker for your platform (on Windows and Mac use [Docker Desktop](https://www.docker.com/products/docker-desktop/))

## Build Image

The following instructions are for _building_ on Apple silicon (tested on an M3).

Replace `<username>` with a local name of your choosing or your Dockerhub username if pushing to Dockerhub.

Run the following to build for Apple silicon locally.

```
docker build --platform=linux/arm64 --rm=true -t <username>/swashbuckling-r:arm64 .
```

Run the following commands to build cross-platform (linux amd64 and linux arm64), pushing to a container registry, an image that can be run on an amd64 Linux machine or Apple silicon.

```
docker login
docker buildx create --use
docker buildx build --platform linux/amd64,linux/arm64 --rm=true -t <username>/swashbuckling-r --push .
```

Note, the base image does not have a build for darwin/amd64, but can still work when using the flag `--platform=linux/amd64` on Intel-based Macs.

Run the image as above in the Quickstart section on the main repo README.md.


## Stop Container and Clean Up

To stop the container (this will keep the state of packages and files):

```
docker stop rstudio_server
```

To remove the container from Docker (note, this will **not** save any installed packages, however the host files loaded into RStudio will be preserved in their latest state as long as the volume was mounted/shared):

```
docker rm rstudio_server
```

## Restart the Server

To start a bash session for the running container:
```
docker exec -it rstudio_server /bin/bash
```

In the bash session:
```
service rstudio-server restart
exit
```

## Additional Links

- [Multi-platform images](https://docs.docker.com/build/building/multi-platform/)
- [Faster Multi-Platform Builds: Dockerfile Cross-Compilation Guide](https://www.docker.com/blog/faster-multi-platform-builds-dockerfile-cross-compilation-guide/)

