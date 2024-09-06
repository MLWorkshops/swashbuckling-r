# Swashbucklin' Data Science: Navigatin' R fer Talk Like a Pirate Day!


## Quickstart for using Docker

- Prerequisites
  - Docker for your platform (on Windows and Mac use [Docker Desktop](https://www.docker.com/products/docker-desktop/))

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

- Login to RStudio
  - Log in to RStudio (at [http://localhost:8989/](http://localhost:8989/)) with username "rstudio" and the password that you gave above and start having fun.


