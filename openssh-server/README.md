# OpenSSH Server

```sh
docker build -t openssh-server .
docker run --rm -it -p 2222:22 openssh-server
```

In another container, run:

```sh
ssh root@localhost -p 2222
# and then enter the password
```
