# Docker

Here will put show note about docker.

## Introduction

- Image
- Container
- Repository

### Image

An image is a read-only template with instructions for creating a Docker container.

### Container

A container is a runnable instance of an image.

Like a sample environment like Linux.

A container is defined by its image as well as any configuration options you provide to it when you create or start it.

### Repository

Repository is a place where image files stored.

- Public: [Docker Hub](https://hub.docker.com/) & [Docker pool](http://www.dockerpool.com/)
- Private

## Install

- Install [Docker Desktop](https://docs.docker.com/desktop/install/windows-install/) on Windows, MAC or Linux
- Using Bash Command on Ubuntu
  - By default
  
  ```bash
  sudo apt update
  sudo apt install -y docker.io
  sudo ln -sf /usr/bin/docker.io /usr/local/bin/docker
  sudo sed -i '$acomplete -F _docker docker' /etc/bash_completion.d/docker
  ```

  - By curl adn sh

  ```bash
  curl -sSL https://get.docker.com/ubuntu/ | sudo sh
  ```

After installation, restart Docker service:

```bash
sudo service docker start
```

## Command

See more details about [Docker command line](https://docs.docker.com/engine/reference/commandline/cli/).

- Pull a image from Docker Hub

  ```bash
  sudo docker pull <Image Name: Tag>
  ```

- Show image files in local

  ```bash
  sudo docker images
  ```

- Run (Create and Start)

  Using Run to create a new Container by Image.

  ```bash
  sudo docker run [OPTIONS] <Image> [COMMAND] [ARG...]
  ```

  - Option:
    - -it: run the Container in interactive mode
    - -d: run the Container in background
    - -p: port
    - [See More](https://www.runoob.com/docker/docker-run-command.html)

- Check all Container

  It will show all Container state and .

  ```bash
  sudo docker ps -a
  ```

- Start a stopped Container

  ```bash
  sudo docker start <Container ID>
  ```

- Stop a Container

  ```bash
  sudo docker stop <Container ID>
  ```

- Into the Container after starting

  ```bash
  sudo docker exec [OPTIONS] <Container ID> <COMMAND> [ARG...]
  ```
  
  See more information about [docker exec](https://docs.docker.com/engine/reference/commandline/exec/).

- Save and load image

  - Save

    ```bash
    sudo docker save -o <file.tar> <Image Name: Tag>
    ```
  
  - Load

    ```bash
    sudo docker load --input <file.tar>
    ```

- Remove

  - Image
  
    ```bash
    sudo docker rmi <Image Name: Tag>
    ```

  - Container
  
    ```bash
    sudo docker rm <Container ID>
    ```

## Reference

- [Docker -- 從入門到實踐](https://philipzheng.gitbook.io/docker_practice/)
- [Docker Docs](https://docs.docker.com/)
- [Docker 菜鳥教程](https://www.runoob.com/docker/docker-tutorial.html)
