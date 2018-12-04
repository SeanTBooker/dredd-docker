<h1 align="center">Dredd in Docker</h1>
<h3 align="center">
    DockerHub: <a href="https://hub.docker.com/r/apiaryio/dredd/">apiaryio/dredd</a>
</h3>
<p align="center">
    <img src="https://travis-ci.org/apiaryio/dredd-docker.svg?branch=master" alt="Travis CI Build Status">
    <img src="https://img.shields.io/docker/build/apiaryio/dredd.svg" alt="Docker Build Status">
    <img src="https://img.shields.io/docker/pulls/apiaryio/dredd.svg" alt="Docker Pulls">
    <img src="https://img.shields.io/docker/stars/apiaryio/dredd.svg" alt="Docker Stars">
</p>

Dredd is an HTTP API testing tool. You can find out more about it at [its documentation](https://dredd.org) or its [code repository](https://github.com/apiaryio/dredd). This repository contains [Docker](https://www.docker.com/) setup for Dredd in form of a `Dockerfile` and the tooling necessary to regularly publish a Docker image with the latest Dredd version available.

## How to run Dredd using Docker?

Following line runs the `dredd` command using the `apiaryio/dredd` Docker image:

```shell
docker run -it -v $PWD:/api -w /api apiaryio/dredd dredd
```

As an example of how to pass arguments, following line runs the `dredd init` command:

```shell
docker run -it -v $PWD:/api -w /api apiaryio/dredd dredd init
```

### Windows

Getting following error?

```
Error response from daemon: create $PWD: "$PWD" includes invalid characters for a local volume name, only "[a-zA-Z0-9][a-zA-Z0-9_.-]" are allowed. If you intended to pass a host directory, use absolute path.
```

The `$PWD:/api` part of the command doesn't work on Windows. Use absolute path instead or try if `${pwd}:/api` does the trick:

```shell
C:\Users\Susan> docker run -it -v ${pwd}:/api -w /api apiaryio/dredd dredd
```

## How does this repository work?

This repository has [Travis CI builds](travis-ci.org/apiaryio/dredd-docker) set up. Travis CI supports setting a [cron build](https://docs.travis-ci.com/user/cron-jobs/), which triggers every day. This build ensures the Dredd image isn't behind the latest Dredd version for more than one day.
