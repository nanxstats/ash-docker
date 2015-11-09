# ash-docker

`ash-docker` provides a Docker image for reproducing the simulation, analysis,
and paper of the [ash](https://github.com/stephens999/ash/) project,
It is also a production-ready environment for running [ashr](https://github.com/stephens999/ashr/).
The Docker image is built on
[ash-packrat](https://github.com/stephenslab/ash-packrat).

## Installation

* [Install Docker](https://docs.docker.com/installation/).

* Download the `ash-docker` image and run a container named `ash`:

        docker pull road2stat/ash-docker

## Reproduce the simulation studies, analysis, and paper

Run `make` to generate the simulation results, analysis, paper, and make them available in a folder accessible from the host:

        cd /home/user/
        mkdir ash-docker-share
        docker run -v /home/rstudio/:/home/user/ash-docker-share --name ash road2stat/ash-docker make

> Note 1: replace `user` with your system user name.

> Note 2: running this will take several hours.

## Reproduce the analysis interactively

        docker run -d -p 8787:8787 --name ash road2stat/ash-docker

* Go to [http://localhost:8787](http://localhost:8787), use `rstudio`/`rstudio`
to log in to the RStudio Server. Compile and interact with the R Markdown
documents in the `analysis/` directory.

## Clean Up

* To stop and remove the running container `ash`:

        docker stop ash
        docker rm ash

* To remove the `ash-docker` image:

        docker rmi road2stat/ash-docker
