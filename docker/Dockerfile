FROM rocker/rstudio:4.4.1
MAINTAINER Micheleen Harris

ARG DEBIAN_FRONTEND=noninteractive
ARG bioc_ver=3.19

RUN apt-get clean all && \
    apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
        build-essential \
        libhdf5-dev \
        libcurl4-gnutls-dev \
        libssl-dev \
        libxml2-dev \
        libpng-dev \
        libxt-dev \
        zlib1g-dev \
        libbz2-dev \
        liblzma-dev \
        libglpk40 \
        libgit2-dev \
        wget \
        cmake \
        gcc \
    && apt-get clean all && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN Rscript -e "install.packages(c('rmarkdown', 'tidyverse', 'workflowr', 'devtools'));"
RUN Rscript -e "install.packages(c('doParallel', 'foreach', 'Rdpack'));"
RUN Rscript -e "install.packages(c('ggrepel', 'ggbeeswarm', 'GGally', 'patchwork');"
RUN Rscript -e "install.packages('BiocManager');"
RUN Rscript -e "BiocManager::install(version = '${bioc_ver}');"
RUN Rscript -e "BiocManager::install(version = 'limma');"

WORKDIR /home/rstudio
