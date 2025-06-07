# OpenSSH Server

Build and run the container:

```sh
sudo apt-get update && sudo apt-get install -y pwgen
SSH_PASSWORD=$(pwgen 20 1)
docker build -t openssh-server --build-arg SSH_PASSWORD="${SSH_PASSWORD}" .
echo "SSH_PASSWORD: ${SSH_PASSWORD}"
docker run --rm -it -p 2222:22 openssh-server
```

In another container, run:

```sh
ssh -p 2222 root@localhost
# or the following to avoid key error
ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null -p 2222 root@localhost
# and then enter the password
```
