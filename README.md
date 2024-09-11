# Docker-Help
Docker management and useful commands

| Command | Description |
| --- | --- |
| `docker build -t custom-exporter:v0.0.1 .` | docker image building from Dockerfile |
| `docker run -d -p 8000:8000 --name "custom-exporter" custom-exporter:v0.0.1.` | docker run the image file in a detached mode |
| `docker tag custom-exporter:v0.0.1 test/custom-exporter:v0.0.1.` | docker image pushing process to docker hub |
| `docker push test/custom-exporter:v0.0.1` | docker image pushing process to docker hub |
| `docker run -d --rm -p 55800:8000(default_port) --name custom-exporter test/custom-exporter:v0.0.1t` | running docker container with neccessary flags |
| `docker buildx create --name mybuilder --use.` | in case, mac env built docker image doesn't work in Linux env |
| `docker buildx inspect --bootstrap` | in case, mac env built docker image doesn't work in Linux env |
| `docker buildx build --platform linux/amd64 -t yourusername/custom-exporter:v0.0.1 --push .` | push to docker hub |
| `docker logs -f --tail 20 container_id` | check docker container logs with 20 log lines limit |
| `docker compose logs -f --tail 20` | check docker compose logs with 20 log lines limit |
| `docker rm $(docker ps -aq)` | remove all unused docker containers |


## Troubleshooting

- Sometimes quitting the `Docker` in `MacOS` doesn't work successfully! In this case you can follow these:
  - Check the process running the docker service
  ```
  ps aux | grep docker
  # then you'll see something similar to this
  USER 14065   0.0  0.2 411036256  33760   ??  S     6:07PM   0:00.05 /Applications/Docker.app/Contents/MacOS/Docker
  ```
  - Then firstly try to kill the `PID` as following
    ```
    #  kill -9 PID
    kill -9 14065
    ```
  - After running the command, check one more time for the Docker process, if it still exists which means that the Docker application is being restarted automatically by another process
    ```
    # then simply run the following command
    pkill -f Docker
    ```
-----------------------------------------------------------------
-----------------------------------------------------------------
- To extract the `executable binary` from Docker image follow this:
  - pull the docker image file:
```
docker pull ghcr.io/unionlabs/uniond-release:v${TAG}
```
  - then search for binary uniond in nix store with following command
```
sudo find /var/lib/docker/ -name "uniond" | grep $(uname -m)
```
  - then copy the executable binary to your destination (ready for use)
------------------------------------------------------------------
-----------------------------------------------------------------
- To work inside the docker container run the following command:
  ```
  docker run -it --rm --name horcrux-container -v /path/to/your/local/directory:/data ghcr.io/strangelove-ventures/horcrux:union-v0.24 /bin/sh
  ```
------------------------------------------------------------------
-----------------------------------------------------------------
- While working inside the docker container, to copy contents inside and outside the container, run the following command:
  ```
  docker cp /path/to/your/local/directory/test.txt horcrux-container:/data/test.txt
  ```
------------------------------------------------------------------
-----------------------------------------------------------------
