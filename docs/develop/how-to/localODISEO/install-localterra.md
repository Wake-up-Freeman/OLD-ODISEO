# Install LocalODISEO

## Prerequisites

- [Docker](https://www.docker.com/)
- [`docker-compose`](https://github.com/docker/compose)
- Supported known architecture: x86_64

## Installation

1. Run the following commands:

    ```sh
    $ git clone --depth 1 https://www.github.com/ODISEOmoney/LocalODISEO
    $ cd LocalODISEO
    ```

2. Make sure your Docker daemon is running in the background and [`docker-compose`](https://github.com/docker/compose) is installed.

## Using LocalODISEO

### Start

```sh
$ docker-compose up
```

Your environment now contains:

- [ODISEOd](http://github.com/ODISEOmoney/core) RPC node running on `tcp://localhost:26657`
- LCD running on http://localhost:1317
- [FCD](http://www.github.com/ODISEOmoney/fcd) running on http://localhost:3060
- An oracle feeder feeding live prices from mainnet, trailing by one vote period

### Stop

```sh
$ docker-compose stop
```

### Reset

```sh
$ docker-compose rm
```
