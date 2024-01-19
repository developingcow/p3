Group Members: Hong

https://github.com/developingcow/p3

This repo is a simple todoapp with a Dockerfile that builds the project and puts it in container that's runnable

Source for source code: https://github.com/tastejs/todomvc

When you build with dockerfile, it will
1. Compile the project
2. Copy over files in /dist folder
3. Ship the /dist content as a nginx container which runs on port 80 when container is launched
   
For this project, we're building for 2 architecture (linux/amd64, linux/arm64)

Steps:
```
docker run --privileged --rm tonistiigi/binfmt --install all
docker buildx create --use --name builder
docker buildx build --platform linux/amd64,linux/arm64 --push -t <repo> .
```

The steps above will push the image to DockerHub <repo> specified.

To use the image,

1. Install docker, start docker service (if havent)
2. `docker run -it -p 80:80 <repo>`
3. <host-ip>:80 will give you the webpage deployed
