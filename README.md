# docker-rexray
Run rexray service in docker
I created this container to run [rexay](https://github.com/emccode/rexray) on coreos with openstack disks.
It is not yet supported because of this bug [#246](https://github.com/emccode/rexray/issues/246)

It has been tested on OVH openstack service [Public cloud](https://www.ovh.com/fr/cloud/)

# Quick start
Launch the container with your openstack credential

    docker run -d --name=rexray --privileged -p 7979:7979
    -v /run/docker/plugins:/run/docker/plugins \
    -v /var/lib/rexray:/var/lib/rexray:shared \
    -v /var/run/rexray:/var/run/rexray \
    -v /dev:/dev \
    -e "OSTACK_AUTH_URL=https://XXXX/" \ 
    -e "OSTACK_USERNAME=XXXXXX" \
    -e "OSTACK_PASSWORD=XXXXXX" \
    -e "OSTACK_TENANT=XXXXXX" \
    -e "OSTACK_REGION=XXX" \
    bretif/rexray

# Prerequisites
You need at least docker version 1.10 in order to enable option `MountFlags=shared` in docker daemon
