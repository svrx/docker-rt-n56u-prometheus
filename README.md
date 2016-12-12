# docker-rt-n56u-prometheus

[Prometheus](http://prometheus.freize.net/) is an interactive script for customizing, compiling, and updating [padavan/rt-n56u](https://bitbucket.org/padavan/rt-n56u). You can use Prometheus to build and flash padavan/rt-n56u to any router given the proper config.

## Docker pull

This will pull an image with padavan/rt-n56u, a built MIPSel toolchain, and Prometheus:

    $ docker pull rwanyoike/rt-n56u-prometheus

To start a Prometheus container:

    $ docker run -it rwanyoike/rt-n56u-prometheus

# Manual build

First, build the [docker-rt-n56u](https://github.com/rwanyoike/docker-rt-n56u) Docker image.

Clone and enter the repo:

    $ git clone https://github.com/rwanyoike/docker-rt-n56u-prometheus
    $ cd docker-rt-n56u

Edit the `latest/Dockerfile` file to use our local `rt-n56u:latest` image:

    $ sed -i '' 's#rwanyoike/rt-n56u#rt-n56u:latest#' latest/Dockerfile

Execute `docker build`:

    $ cd latest
    $ docker build -t rt-n56u-prometheus:latest .

The [Dockerfile](https://github.com/rwanyoike/docker-rt-n56u-prometheus/blob/master/latest/Dockerfile) will download Prometheus and set it up.

When we list our Docker images on the host:

    $ docker images

    REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
    rt-n56u-prometheus  latest              bfbd1ecc2aec        38 minutes ago      3.785 GB
    rt-n56u             latest              12be11919d36        14 hours ago        3.703 GB
    debian              jessie              ddf73f48a05d        2 weeks ago         123 MB

We'll have our image `rt-n56u-prometheus:latest`.
