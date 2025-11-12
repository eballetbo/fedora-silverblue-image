
podman build -t centos-kernel-builder .

podman run -it --rm -v $(pwd):/usr/src:Z centos-kernel-builder
