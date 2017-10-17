# docker-alpine-collectd

An alpine based image with collectd.

By default, the image writes metrics to stdout, which is only useful for
debugging. Users are supposed to provide their own configuration by mounting a
config file:

    $ touch collectd.conf  # edit to suit your own needs
    $ docker run \
        --privileged \
        -v /proc:/proc:ro \
        -v `pwd`/collectd.conf:/etc/collectd/collectd.conf \
        collectd-alpine

Note `--privileged` is necessary to allow the container to collect metrics of
the host, instead of the container itself.
