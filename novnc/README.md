# noVNC

Build and run the container:

```sh
docker build -t novnc .
docker run --name novnc --rm -it --network=host novnc
```

Open <http://localhost:6080> in your browser and click "Connect".

Or you can specify the VNC server address: <http://localhost:6080/?host=localhost&port=5900>.

This assumes you have a VNC server running on `localhost:5900`.

You can adjust the screen size using `Settings > Scaling Mode`. The `Clipboard` feature is also available when needed.
