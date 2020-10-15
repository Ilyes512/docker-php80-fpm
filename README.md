# docker-php80-fpm

A PHP 7.0 based Docker base image.

[![Status Latest Alpine-based](https://github.com/Ilyes512/docker-php80-fpm/workflows/Build%20latest%20Alpine%20images/badge.svg)](https://github.com/Ilyes512/docker-php80-fpm/actions?query=workflow%3A%22Build+latest+Alpine+images%22)
[![Status Latest Debian-based](https://github.com/Ilyes512/docker-php80-fpm/workflows/Build%20latest%20Debian%20images/badge.svg)](https://github.com/Ilyes512/docker-php80-fpm/actions?query=workflow%3A%22Build+latest+Debian+images%22)

## Pulling the images

```
# Alpine based
docker pull ilyes512/php80-fpm:alpine-latest-builder
docker pull ilyes512/php80-fpm:alpine-latest-runtime

# Debian based
docker pull ilyes512/php80-fpm:debian-latest-runtime
docker pull ilyes512/php80-fpm:debian-latest-runtime
```

The tag scheme: `{OS}-{VERSION}-{TARGET}`

- **{OS}**: `alpine` or `debian`
- **{VERSION}**: `latest` or tag i.e. `1.0.0`
- **{TARGET}**: `runtime` or `builder`

## Building the docker image(s)

There are 2 targets at the moment:

  - **runtime**: this is for *production*. It does not contain any development tools like Composer and Xdebug.
  - **builder**: this is for *development*. This is based on the runtime-target and it adds Composer, Xdebug etc.

Building runtime-target:

```
docker build --tag ilyes512/php80-fpm:alpine-latest-runtime --file alpine/Dockerfile --target runtime .

docker build --tag ilyes512/php80-fpm:debian-latest-runtime --file alpine/Dockerfile --target runtime .
```

Building builder-target:

```
docker build --tag ilyes512/php80-fpm:alpine-latest-builder --file debian/Dockerfile --target builder .

docker build --tag ilyes512/php80-fpm:debian-latest-builder --file debian/Dockerfile --target builder .
```

## Task commands

Available [Task](https://taskfile.dev/#/) commands:

```
task: Available tasks for this project:

* d:build:alpine:       Build a PHP Alpine-based Docker image
* d:build:debian:       Build a PHP Debian-based Docker image
* d:lint:               Apply a Dockerfile linter (https://github.com/hadolint/hadolint)
```