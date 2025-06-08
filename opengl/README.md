# OpenGL

Build and run the container:

```sh
docker build -t opengl .
xhost +local:docker
docker run --name opengl --rm -it --gpus all --network=host \
  -e DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  -v $HOME/.Xauthority:/root/.Xauthority \
  --device /dev/dri:/dev/dri \
  opengl
```

In the container, run:

```sh
glxinfo | grep OpenGL
glxgears
```

If OpenGL is using integrated GPU, run the following to use discrete GPU:

```sh
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia glxinfo | grep OpenGL
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia glxgears
```
