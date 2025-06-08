# Code Server

Build and run the container:

```sh
sudo apt-get update && sudo apt-get install -y pwgen
CODE_SERVER_PASSWORD=$(pwgen 20 1)
docker build -t code-server --build-arg CODE_SERVER_PASSWORD="${CODE_SERVER_PASSWORD}" .
echo "CODE_SERVER_PASSWORD: ${CODE_SERVER_PASSWORD}"
docker run --name code-server --rm -it -p 8080:8080 code-server
```

Open <http://localhost:8080> in your browser and enter the password.

Or you can specify the folder path: <http://127.0.0.1:8080/?folder=/>.
