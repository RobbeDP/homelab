# Homelab

## Requirements

- [Docker Engine](https://docs.docker.com/engine/)
- [Docker Compose](https://docs.docker.com/compose/)

## Setup

Create a Docker network named `proxy` if it does not already exist:

```sh
docker network inspect proxy >/dev/null 2>&1 || docker network create proxy
```

For each service directory that includes an `.env.example` file, copy it to `.env` and update the values as needed:

```sh
for dir in ./*; do
  [ -d "$dir" ] || continue
  [ -f "$dir/.env.example" ] || continue
  [ -f "$dir/.env" ] || cp "$dir/.env.example" "$dir/.env"
done
```

## Start a service

Change into the directory of the service you want to run, then start it with Docker Compose:

```sh
cd <service-dir>
docker compose up -d
```
