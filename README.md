Docker Stacks
=============
*Currated Docker images for use with Jupyter and [Pangeo](http://pangeo.io/)*

[![Build Status](https://travis-ci.org/pangeo-data/pangeo-stacks.svg?branch=master)](https://travis-ci.org/pangeo-data/pangeo-stacks)

This repository contains a few currated Docker images that can be used with deployments of the [Pangeo Helm Chart](https://github.com/pangeo-data/helm-chart). Each of the images in this repository are configured and built using [repo2docker](https://repo2docker.readthedocs.io) and are continuously deployed to DockerHub. Importantly, each image built in this repo includes the minimum required libraries to do scalable computations with Pangeo (via dask-kubernetes).

### Current Notebook Images:

| Image           | Description                                   | Link | Badges  |
|-----------------|-----------------------------------------------|------|---------|
| base-notebook   | A bare-bones image with Jupyter and Dask.     | [DockerHub](https://hub.docker.com/r/pangeo/base-notebook) | [![](https://img.shields.io/docker/pulls/pangeo/base-notebook.svg)](https://hub.docker.com/r/pangeo/base-notebook) [![](https://images.microbadger.com/badges/image/pangeo/base-notebook.svg)](https://microbadger.com/images/pangeo/base-notebook "Get your own image badge on microbadger.com")[![](https://images.microbadger.com/badges/version/pangeo/base-notebook.svg)](https://microbadger.com/images/pangeo/base-notebook "Get your own version badge on microbadger.com")     |
| pangeo-notebook | A complete image with lots of Python packages | [DockerHub](https://hub.docker.com/r/pangeo/pangeo-notebook) | [![](https://img.shields.io/docker/pulls/pangeo/pangeo-notebook.svg)](https://hub.docker.com/r/pangeo/pangeo-notebook) [![](https://images.microbadger.com/badges/image/pangeo/pangeo-notebook.svg)](https://microbadger.com/images/pangeo/pangeo-notebook "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/pangeo/pangeo-notebook.svg)](https://microbadger.com/images/pangeo/pangeo-notebook "Get your own version badge on microbadger.com") |

### Adding new images

It is easy to add additional images. The basic steps involved are:

1. Open an [Issue](https://github.com/pangeo-data/pangeo-stacks/issues/new) to discuss adding your image.
2. Copy the `base-notebook` directory and name it something informative.
3. Modify the contents of the `binder` directory, adding any configuration you need according to the [repo2docker documentation](https://repo2docker.readthedocs.io/en/latest/config_files.html).
4. Edit the TravisCI configuration file to inclue the new image.
5. Push your changes to GitHub and open a Pull Request.

### CI/CD

The images in Pangeo-stacks are built and deployed continuously using [TravisCI](https://travis-ci.org/pangeo-data/pangeo-stacks). Images are versioned using the [CALVER](https://calver.org/) system.

### Build locally
The images here can be built locally using [repo2docker](https://repo2docker.readthedocs.io). The following example demonstrates how to build the `base-notebook` image:

```shell
repo2docker --no-run --user-name=jovyan --user-id 1000 \
    --appendix="`cat appendix.txt`" \
    --image-name=pangeo/base-notebook ./base-notebook
```

### Related projects

- [Jupyter/docker-stacks](https://github.com/jupyter/docker-stacks): Ready-to-run Docker images containing Jupyter applications
- [repo2docker](https://repo2docker.readthedocs.io): A tool to build, run, and push Docker images from source code repositories that run via a Jupyter server
- [Pangeo Helm Chart](https://github.com/pangeo-data/helm-chart): The helm chart for installing Pangeo.
