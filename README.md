# Snell Server

[![Build Status](https://github.com/funnyzak/snell-server-docker/actions/workflows/docker_build.yml/badge.svg)](https://github.com/funnyzak/snell-server-docker/actions)
[![Image Size](https://img.shields.io/docker/image-size/funnyzak/snell-server)](https://hub.docker.com/r/funnyzak/snell-server/)
[![Docker Stars](https://img.shields.io/docker/stars/funnyzak/snell-server.svg?style=flat-square)](https://hub.docker.com/r/funnyzak/snell-server/)
[![Docker Pulls](https://img.shields.io/docker/pulls/funnyzak/snell-server.svg?style=flat-square)](https://hub.docker.com/r/funnyzak/snell-server/)
[![Docker Tags](https://img.shields.io/docker/v/funnyzak/snell-server?sort=semver&style=flat-square)](https://hub.docker.com/r/funnyzak/snell-server/)

This image is built for [snell server](https://manual.nssurge.com/others/snell.html), which is a lean encrypted proxy protocol. If you want to use **Snell Client**, please download from [NSSurge](https://nssurge.com/).

This image supports `linux/amd64`, `linux/arm64`, `linux/arm/v7` and `linux/386` architecture. The latest version is `v4.1.0`.

> The latest surge-server version is v4, which is not compatible with the previous versions like before. Please upgrade both the client (Surge iOS & Surge Mac) and the server binary.

## Docker Pull

`docker pull funnyzak/snell-server:latest`

Or chinese mirror:

`docker pull registry.cn-beijing.aliyuncs.com/funnyzak/snell-server:latest`

## Docker Run

Your can run this image with the following command:

```bash
# One line command
docker run -d --name snell-server --restart always -p 12303:6180 -e PSK="5G0H4qdf32mEZx32t" funnyzak/snell-server

# Or with environment variables
docker run -d --name snell-server --restart always \
  -e PSK="5G0H4qdf32mEZx32t" \
  -e TZ="Asia/Shanghai" \
  -e IPV6="false" \
  -e PORT=6180 \
  -p 12303:6180 funnyzak/snell-server:latest

# Echo config file
docker exec -it snell-server cat /app/snell-server.conf
```

Or you can use docker-compose to run this image:

```yaml
version: '3'
services:
  snell:
    image: funnyzak/snell-server
    container_name: snell-server
    environment:
      PSK: 5G0H4qdf32mEZx32t
      TZ: Asia/Shanghai
      IPV6: false
      PORT: 6180
    restart: always
    ports:
      - 12303:6180
```

## Reference

- [Snell Server](https://manual.nssurge.com/others/snell.html)

## License

[MIT](LICENSE)