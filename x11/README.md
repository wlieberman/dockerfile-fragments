# X11

Build and run the container:

```sh
docker build -t x11 .
xhost +local:docker
docker run --name x11 --rm -it --network=host \
  -e DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  -v $HOME/.Xauthority:/root/.Xauthority \
  x11
```

In the container, run:

```sh
xdpyinfo
xclock
```
