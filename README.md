# ash-docker

ash-docker provides a Docker image for reproducing the analysis of the
[ash](https://github.com/stephens999/ash/) project, and an production-ready
environment for running [ashr](https://github.com/stephens999/ashr/).
The Docker image is built mostly based on
[ash-packrat](https://github.com/stephenslab/ash-packrat).

## Install

* [Install Docker](https://docs.docker.com/installation/).

* Download the ash-docker Docker image and run a container named `ash`:

        docker pull road2stat/ash-docker

## Reproduce the simulation studies

Run `make` under `code/` and make output files available in host:

        docker run -v /home/rstudio/output:/home/hostusername/output --name ash road2stat/ash-docker cd code && make

Note running this will take hours.

## Reproduce the analysis interactively

        docker run -d -p 8787:8787 --name ash road2stat/ash-docker

* Go to [http://localhost:8787](http://localhost:8787), use `rstudio`/`rstudio`
to log in to the RStudio Server. Compile and interact with the R Markdown
documents in the `analysis/` directory, or run `system("make")`.

## Cleaning

* To stop and remove the running container `ash`:

        docker stop ash
        docker rm ash

* To remove the `ash-docker` image:

        docker rmi road2stat/ash-docker
