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
