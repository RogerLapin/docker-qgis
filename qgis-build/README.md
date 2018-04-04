# qgis-build

This directory includes a Dockerfile for building the `qgis-build` Docker image, which includes
all the tools and libraries necessary for building QGIS from source. 
It is devoted to build version 2.18.18 of qgis-server, and has not been tested for sooner version.
It is not suited to later versions of qgis (3+) since many dependencies havec changed (Pyton+, Qt+, etc.)

## Build the image

```shell
$ docker build -t qgis-build .
```

## Build QGIS

Create a `build` directory and place the QGIS source tree in that directory. Do not create it under
the `qgis-build` directory (or under a sub-directory of `qgis-build`), otherwise the QGIS source
tree will be part of the Docker context and building the image again will take a lot of time.

```shell
$ mkdir build
$ cd build
$ git clone https://github.com/qgis/QGIS.git
$ git fetch
$ cd docker-qgis/qgis-build
```

Build the `qgis-build` Docker image:


```

Build QGIS:

```shell
$ docker run -it --rm -v $(pwd):/qgis -u $(id -u):$(id -g) qgis-build
```

Note that the `docker run` command should be run from the `build` directory, that is the directory
that contains the `QGIS` repository.

Notes:

* `-v $(pwd):/qgis` is used to mount the current directory (`build`) into `/qgis` in the container
* `-u $(id -u):$(id -g)` is used to use the local user id and group id within the container

After the build completes you should find Debian packages (`.deb` files) in the `build` directory.
