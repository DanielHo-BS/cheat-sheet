# Docker

A comprehensive guide to Docker fundamentals and usage.

## Configuration Guides

- [Docker on WSL](./dockerWSL.md) - Setup and usage on Windows Subsystem for Linux
- [Change Storage Path](./storePath.md) - Modify where Docker stores its data
- [Docker Compose](./compose.md) - Multi-container Docker applications

## Contents

- [Docker](#docker)
  - [Configuration Guides](#configuration-guides)
  - [Contents](#contents)
  - [Introduction](#introduction)
    - [Core Concepts](#core-concepts)
      - [Image](#image)
      - [Container](#container)
      - [Repository](#repository)
  - [Installation](#installation)
    - [Windows, macOS, or Linux Desktop](#windows-macos-or-linux-desktop)
    - [Ubuntu Server (CLI)](#ubuntu-server-cli)
      - [Method 1: Using apt](#method-1-using-apt)
      - [Method 2: Using installation script](#method-2-using-installation-script)
  - [Common Commands](#common-commands)
    - [Image Management](#image-management)
    - [Container Management](#container-management)
  - [References](#references)

## Introduction

Docker is a platform for developing, shipping, and running applications in isolated environments called containers.

### Core Concepts

#### Image
An image is a read-only template containing instructions for creating a Docker container. Images include the application code, libraries, dependencies, tools, and other files needed to run an application.

#### Container
A container is a runnable instance of an image. It's a lightweight, standalone, executable package that includes everything needed to run an application. Containers isolate software from its surroundings and ensure it works uniformly across different environments.

#### Repository
A repository is a storage location for Docker images.

- **Public repositories**: [Docker Hub](https://hub.docker.com/) and [Docker Pool](http://www.dockerpool.com/)
- **Private repositories**: Self-hosted or cloud-based private registries

## Installation

### Windows, macOS, or Linux Desktop
Install [Docker Desktop](https://docs.docker.com/desktop/install/windows-install/) for a complete Docker development environment with GUI.

### Ubuntu Server (CLI)

#### Method 1: Using apt
```bash
sudo apt update
sudo apt install -y docker.io
sudo ln -sf /usr/bin/docker.io /usr/local/bin/docker
sudo sed -i '$acomplete -F _docker docker' /etc/bash_completion.d/docker
```

#### Method 2: Using installation script
```bash
curl -sSL https://get.docker.com/ubuntu/ | sudo sh
```

After installation, start the Docker service:
```bash
sudo service docker start
```

## Common Commands

### Image Management
```bash
# Pull an image from Docker Hub
sudo docker pull <image-name>:<tag>

# List local images
sudo docker images

# Save image to a tar file
sudo docker save -o <filename.tar> <image-name>:<tag>

# Load image from a tar file
sudo docker load --input <filename.tar>

# Remove an image
sudo docker rmi <image-name>:<tag>
```

### Container Management
```bash
# Create and start a container
sudo docker run [OPTIONS] <image> [COMMAND] [ARG...]
# Common options:
#   -it: Interactive mode with terminal
#   -d: Run in background (detached)
#   -p <host-port>:<container-port>: Port mapping
#   --name <container-name>: Assign a name

# List running containers
sudo docker ps

# List all containers (including stopped)
sudo docker ps -a

# Start a stopped container
sudo docker start <container-id>

# Stop a running container
sudo docker stop <container-id>

# Execute a command in a running container
sudo docker exec [OPTIONS] <container-id> <command>
# Common options:
#   -it: Interactive mode with terminal

# Remove a container
sudo docker rm <container-id>
```


## References

- [Docker Documentation](https://docs.docker.com/)
- [Docker -- 從入門到實踐](https://philipzheng.gitbook.io/docker_practice/)
- [Docker Tutorial](https://www.runoob.com/docker/docker-tutorial.html)
