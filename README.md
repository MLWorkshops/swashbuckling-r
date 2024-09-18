# Swashbucklin' Data Science: Navigatin' R fer Talk Like a Pirate Day!

Ahoy, matey, and welcome to our workshop repo!

## Get the code

To get the code, you can either `git clone` this repo or download it as a zip file to get the code, e.g.,

```
git clone https://github.com/MLWorkshops/swashbuckling-r.git
```

If using your own RStudio application, navigate to the `swashbuckling-r` folder from the application.  If you want to use our pre-built docker container that has all of the dependencies installed, keep on reading.

## Quickstart for using Docker

- Prerequisites
  - Docker for your platform (on Windows and Mac use [Docker Desktop](https://www.docker.com/products/docker-desktop/))

1. Open a terminal or command prompt window.

2. Navigate on the command line to the directory with the code (`swashbuckling-r`)

3. Run the docker container.

- Apple Silicon (M-series chip):

```
docker run --name rstudio_server -d -p 8989:8787 -v $PWD:/home/rstudio -e PASSWORD=password  -t rheartpython/swashbuckling-r
```

- Intel Mac:

```
docker run --platform=linux/amd64 --name rstudio_server -d -p 8989:8787 -v $PWD:/home/rstudio -e PASSWORD=password  -t rheartpython/swashbuckling-r
```

- Windows (tested on 11):
  - To run on Windows, the command in Command Prompt will be similar except for the `-v $PWD:/home/rstudio` part which will use Windows environment variable syntax instead (e.g., `-v %CD%:/home/rstudio`), thus the Windows 11 command is as follows in Command Prompt.

```
docker run --name rstudio_server -d -p 8989:8787 -v %CD%:/home/rstudio -e PASSWORD=password  -t rheartpython/swashbuckling-r
```

4. Login to RStudio.
  - Log in to RStudio (at [http://localhost:8989/](http://localhost:8989/)) with username "rstudio" and the password that you gave above and start having fun.

## Stop Container and Clean Up

To stop the container (this will keep the state of packages and files):

```
docker stop rstudio_server
```

To remove the container from Docker (note, this will **not** save any installed packages, however the host files loaded into RStudio will be preserved in their latest state as long as the volume was mounted/shared):

```
docker rm rstudio_server
```

## Restart RStudio Server

To start a bash session for the running container:
```
docker exec -it rstudio_server /bin/bash
```

In the bash session:
```
service rstudio-server restart
exit
```

