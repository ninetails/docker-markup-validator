# Docker W3C Validator (DEPRECATED)

Docker container with W3C Markup Validator ([Nu Html Checker](https://github.com/validator/validator)) and a image based on [`openjdk:8-jre-alpine`](https://hub.docker.com/_/openjdk/).

## Deprecated

Please, use the official image [validator/validator](https://hub.docker.com/r/validator/validator/).

## Usage

### Run

```
docker run --rm -p 8888:8888 -it ninetails/markup-validator
```

It will open validator java server that you can access on browser as `http://localhost:8888/`.

### Using [with DNS](https://docs.docker.com/engine/userguide/networking/configure-dns/)

Sometimes you need to test pages behind a firewall on a private network. Just specify DNS server by using docker run parameter `--dns`.

```
docker run --dns=127.0.0.5 --rm -p 8888:8888 -it ninetails/markup-validator
```

### Running validator on command line

#### with URLs

Pretty straight

```
docker run --rm -it ninetails/markup-validator validator <URL>
```

#### Local files

You need to create a volume (or mount) with docker run and then run `validator` passing path to html file inside on mounted folder.

Example below creating a file named `index.html` and a volume pointed on container as `/test`:

```
docker run --rm -it -v "$(pwd)":/test:ro ninetails/markup-validator validator /test/index.html
```

## Build with a different release version for validator

You will need to build docker image:

```
docker build --build-arg VALIDATOR_RELEASE_VERSION=16.3.3 ninetails/markup-validator
```

## License
This project is licensed under the MIT License - see the LICENSE.md file for details
