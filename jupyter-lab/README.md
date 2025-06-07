# Jupyter Lab

Build and run the container:

```sh
sudo apt-get update && sudo apt-get install -y pwgen
JUPYTER_LAB_TOKEN=$(pwgen 20 1)
docker build -t jupyter-lab --build-arg JUPYTER_LAB_TOKEN="${JUPYTER_LAB_TOKEN}" .
echo "JUPYTER_LAB_TOKEN: ${JUPYTER_LAB_TOKEN}"
docker run --name jupyter-lab --rm -it -p 8888:8888 jupyter-lab
```

Open <http://localhost:8888> in your browser and enter the password.
