# carbon
This container runs the [carbon](https://github.com/graphite-project/carbon)
daemon and that's it.

## Running on Docker

This container expects to listen on three ports and have two mounted volumes.
It needs to listen on port 2003 TCP, 2004 TCP, and 7002 TCP. It needs to have
`/opt/graphite/conf` and `/opt/graphite/storage` mounted.

    docker build -t ghcr.io/uwcip/carbon:latest .
    docker run --rm -it -p 2003:2003/tcp -p 2004:2004/tcp -p 7002:7002/tcp -v $PWD/storage:/opt/graphite/storage -v $PWD/example:/opt/graphite/conf ghcr.io/uwcip/carbon:latest

Example configuration files are provided is in the `example` directory. There
may be more configuration files that you can provide to carbon that are not
present in the examples. You must provide _at least_ `carbon.conf` and
`storage-schemas.conf` or the daemon will not start.
