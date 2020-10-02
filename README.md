# MinIO Dockerized

- [MinIO Dockerized](#minio-dockerized)
  - [Overview](#overview)
  - [Requirements](#requirements)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)

---

## Overview

This repository contains a template to deploy [MinIO](https://min.io/) using [Docker Compose](https://docs.docker.com/compose/) on a single machine running [Docker](https://www.docker.com/).

## Requirements

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Git](https://git-scm.com/)
- Text editor of your choice (e.g. [Vim](https://www.vim.org/))

## Installation

Clone the repository:

```sh
$ git clone https://github.com/cedrichopf/minio-dockerized.git
Cloning into 'minio-dockerized'...
```

Create a copy of the example configuration files:

```sh
# MinIO Configuration
$ cp example.env .env
# Custom Docker Compose Configuration
$ cp override.example.yml docker-compose.override.yml
```

Configure the MinIO deployment by adapting the environment variables in the `.env` file:

```sh
$ vim minio.env
```

Further information about the available environment variables can be found here: [Environment Variables](#environment-variables)

Configure the docker-compose.override.yml file:

```sh
$ vim docker-compose.override.yml
```

**Important:** The example configuration doesn't publish any ports by default. It uses an existing [Traefik](https://containo.us/traefik/) instance as a reverse proxy to access the MinIO instance. If you want to publish ports, please add them to the `docker-compose.override.yml` configuration.

Download the Docker images and start the services using docker-compose:

```sh
$ docker-compose pull
$ docker-compose up -d
```

Open your browser and access your MinIO instance using the URL of the Docker host and the configured route, e.g. [http://127.0.0.1](http://127.0.0.1).

## Environment Variables

The following table contains an overview of the environment variables which can be configured in the `minio.env` file.

| Environment Variable | Example                            | Description                     |
| -------------------- | ---------------------------------- | ------------------------------- |
| COMPOSE_PROJECT_NAME | `minio`                            | Project name for docker-compose |
| MINIO_ACCESS_KEY     | `4c2b0bcec43084442d92837f8e17c50e` | Access Key for MinIO            |
| MINIO_SECRET_KEY     | `b27a0497ad27ea9afbcc0e0026227e3d` | Secret Key for MinIO            |
