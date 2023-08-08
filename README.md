# Hydroxide Dockerfile

This repository provides an example Dockerfile configuration for [hydroxide](https://github.com/emersion/hydroxide).

Before submitting issues, please see the [hydroxide](https://github.com/emersion/hydroxide) docs and [Protomail](https://protonmail.com/support/) support pages for hydroxide and Protonmail specific matters.

I offer no guarentees that this is a secure way to store and pass your hydroxide authentication information to other apps. It is one working example to get you started. If can improve the security of this example configuration, please send a pull request. 

## Running hydroxide as a Docker container

First, you need to run the container and link it to your other apps. You can do this with `docker run` or `docker-compose`.

docker run:

```
docker run -it -d --user 1000 -p 1025:1025 -p 1143:1143 -p 8080:8080 -v hydroxide-data:/hydroxide --name hydroxide ma04/hydroxide:latest serve
```

Ports:
    1025: SMTP server
    1143: IMAP server
    8080: Carddav HTTP server

After running the container, you need to login to your Protonmail account with your proton username. You can do this by running:

```
docker exec -it hydroxide hydroxide auth <proton user name>
```


### IMPORTANT: You must run the container with the `--user 1000`(your user id) flag. This is because the container runs as root by default and hydroxide will not run as root and cause filesystem permission error.

to get your user id, run the following command:

```
id -u
```
## Setup

Below are some basic instructions to get you started.


### docker-compose

If you require a `docker-compose` file, see [docker-compose.yml](docker-compose.yml). If you are unfamiliar with docker-compose, here is some code to get you started.

```

# navigate to this repo by changing the directory
```
cd hydroxide-docker
```

make appropriate changes to the docker-compose.yml file and then run the following commands

```
docker-compose up -d
```

After running the container, you need to login to your Protonmail account with your proton username. You can do this by running:

```
docker exec -it hydroxide hydroxide auth <proton user name>
```


