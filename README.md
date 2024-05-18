# Docker-help
Docker management and useful commands

| Command | Description |
| --- | --- |
| `docker build -t custom-exporter:v0.0.1 .` | docker image building from Dockerfile |
| `docker run -d -p 8000:8000 --name "custom-exporter" custom-exporter:v0.0.1.` | docker run the image file in a detached mode |
| `docker tag custom-exporter:v0.0.1 test/custom-exporter:v0.0.1.` | docker image pushing process to docker hub |
| `docker push test/custom-exporter:v0.0.1` | docker image pushing process to docker hub |
| `docker run -d --rm -p 55800:8000(default_port) --name custom-exporter test/custom-exporter:v0.0.1t` | running docker container with neccessary flags |
- docker buildx create --name mybuilder --use. (in case, mac env built docker image doesn't work in Linux env)
- docker buildx inspect --bootstrap (in case, mac env built docker image doesn't work in Linux env)
- docker buildx build --platform linux/amd64 -t yourusername/custom-exporter:v0.0.1 --push .
- docker logs -f --tail 20 container_id
- docker compose logs -f --tail 20
- docker rm $(docker ps -aq) -> remove all containers
