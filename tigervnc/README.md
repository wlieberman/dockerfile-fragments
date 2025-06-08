# TigerVNC

Build and run the container:

```sh
sudo apt-get update && sudo apt-get install -y pwgen
TIGERVNC_PASSWORD=$(pwgen 20 1)
docker build -t tigervnc . --build-arg TIGERVNC_PASSWORD="${TIGERVNC_PASSWORD}"
echo "TIGERVNC_PASSWORD: ${TIGERVNC_PASSWORD}"
docker run --name tigervnc --rm -it -p 5900:5900 tigervnc
```

Connect to port 5900 with [TigerVNC viewer](https://github.com/TigerVNC/tigervnc/releases).
