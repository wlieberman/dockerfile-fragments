# Vulkan

Build and run the container:

```sh
docker build -t vulkan .
xhost +local:docker
docker run --name vulkan --rm -it --gpus all --network=host \
  -e DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  -v $HOME/.Xauthority:/root/.Xauthority \
  vulkan
```

In the container, run:

```sh
vulkaninfo --summary
vkcube
```

## References

- [j3soon/docker-vulkan-runtime](https://github.com/j3soon/docker-vulkan-runtime)
- [Development Environment :: Vulkan Documentation Project](https://docs.vulkan.org/tutorial/latest/02_Development_environment.html#_vulkan_packages)
- [nvidia/container-images/vulkan](https://gitlab.com/nvidia/container-images/vulkan/-/blob/master/docker/Dockerfile.ubuntu)
- [nvidia/container-images/opengl](https://gitlab.com/nvidia/container-images/opengl)
- [Isaac Sim \| NVIDIA NGC](https://catalog.ngc.nvidia.com/orgs/nvidia/containers/isaac-sim/layers)
