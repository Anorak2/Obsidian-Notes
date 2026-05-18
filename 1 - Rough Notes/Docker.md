## Import Go note:
* You can signify the architecture your go binary is built for so that way when you "dockerize it" it can match what the dockerfile is expecting
* Example:
```bash
# Build go binaries
GOOS=linux GOARCH=amd64 go build

# -----------

# Docker file example:
# Set that this comes from a debian distro
FROM debian:stable-slim

# COPY source destination
COPY learn-docker /bin/learn-docker
CMD ["/bin/learn-docker"]
```

## Basic Commands
* `docker help`: Help menu, all below are present in there
* `build`: Builds image from docker-file
	* Usually a script in CI / CD will use this a lot so you won't manually call to it but the script itself will
* `push / pull`: Push / pull docker image to a registry
	* Pull can be used to tell a kurbenetes cluster to pull in this new docker image
* `exec`: Gets shell session in running container, nice for debugging
	* `-i`: Makes exec interactive
	* `-t`: Gives us a tty (keyboard) interface
	* `docker exec -it CONTAINER_ID /bin/sh`: Gives a shell session inside the container
* `kill / stop`: Sends signals to stop docker containers
* `tag`: Used to tag builds for versioning reasons
* `run`: Used to run containers
	* `--network-none`: Disable network on the container. Useful if running 3rd party code / container has a virus and you want to audit it
		* `docker run -d --network none docker/getting-started`

## Images & Containers
* Images are the read only description / layout of what to run
* Containers are the Read / write environment that runs / is running

## Running
* Use `docker run` to run an image, can use it to spawn multiple containers
	* Flags:
		* `d`: Detached mode (Doesn't block terminal)
		* `p`: publish a containers port to the host (forwarding)
		* `hostport:containerport`: Host is the port on your local machine while container is the port inside the container
		* `namespace/name:tag`: name of image and the tag is the version of the image (Often latest)
		* `-e NODE_ENV=dev`: Allows setting environment variables
		* `-v ghost-vol:/var/lib/ghost`: Mounts a volume to a path in the container so anything used by the app into var lib ghost gets saved to the volume
* Example:
```bash
# this is just an example, don't run this
docker run -d -p hostport:containerport namespace/name:tag

# See running containers
docker ps

# Example of running ghost (docker pull ghost)
docker run -d -e NODE_ENV=development -e url=http://localhost:3001 -p 3001:2368 -v ghost-vol:/var/lib/ghost ghost
```
* To see running containers run `docker ps`

## Persistent state
* If restarting a container it will contain changes made inside of it but if stopping / starting it it will basically be like if you started a fresh one from the image again
* However you can implement [storage volumes](https://docs.docker.com/engine/storage/volumes/) to implement persistent state
* Example:
```bash
# Create an empty volume named ghost-vol
docker volume create ghost-vol

# List volumes
docker volume ls

# Inspect volume to see where it is
docker volume inspect ghost-vol
```

## Load Balancers
* Server that sits in front of backend server and just distributes the work to the backend servers, useful since many cases just 1 server won't be able to handle all the load.
* Can have many load balancers / different layers like global, regional, and local ones as well if popular enough / paying for some AWS thing.
* [Different approaches to distributing from equal load to more](https://www.cloudflare.com/learning/performance/types-of-load-balancing-algorithms/):
	* Round Robin load balancer: Distribute in order A - B - C - A - B - C
	* Weighted round robin: Round robin with weights on servers depending on how much load it can support so that way more powerful get more
	* IP Hash: hashes source / destination IP to find the server to assign it to.
* This relates to docker in the sense that they can pass / load balance to docker images themselves.

## Custom Networks
* You can create a custom network for containers so they can talk to one another but still be isolated to the outside network.
* Example:
```bash
# Create network
docker network create caddytest


# List networks
docker network ls

# Start container attached to network and access it's shell
docker run -it --network caddytest docker/getting-started /bin/sh

# Run container in network with special name
docker run --network caddytest --name caddy1 -d -v "$PWD/index1.html:/usr/share/caddy/index.html:Z" caddy
```
* In the above where we gave it a name `caddy1` this allows us to curl it inside any bridged device by that. So if we do `curl caddy1` it responds appropriately

## Dockerfile
* Dockerfiles are descriptions of an image to make when running the `build` command
* Example:
```c
# This is a comment

# Use a lightweight debian os
# as the base image
FROM debian:stable-slim

# COPY source destination (Copy file learn-docker to this area in the docker container)
COPY learn-docker /bin/learn-docker

# Set an env var
ENV PORT=8991

# execute the 'echo "hello world"'
# command when the container runs
CMD ["echo", "hello world"]
```
* The above defines that this will use Debian as the base image and then it will run the command echo to echo back hello world inside the application. This is basically just a lightweight dockerfile nothing that provides too much use.
* If we run `docker build . -t helloworld:latest` in the directory for this it looks for a Dockerfile and then runs it, the `-t helloworld:latest` bit is a tag, we name the program name to helloword and set the tag bit to latest to signify to users
* If we then run `docker run helloworld` we will see `hello world` echo'd back to us

## Docker Logs
* When running containers in detached mode you don't see output in the terminal so if something goes wrong or what not you can tell using logs
* `docker logs [OPTIONS] CONTAINER`: Container can be id / name

### Stats
* To view stats of a container you can do `docker stats [OPTIONS] [CONTAINER...]` for this a blank `docker stats` will give you stats over all running containers
* To view the processes inside a container you will use the `docker top CONTAINER [ps OPTIONS]` command
* Example:
```bash
# Processes inside a container
docker top CONTAINER [ps OPTIONS]

# Check the processes in the CPU-intensive container
docker top cpu-stress

# Check the processes in the memory-intensive container
docker top mem-stress


# ------
docker stats [OPTIONS] [CONTAINER...]


docker run -d --cpus="0.25" --name cpu-stress alexeiled/stress-ng --cpu 2 --timeout 10m
```
* For this bottom run command we use `--cpus` to limit the "amount" of a CPU core it will use, the `--memory` is used to limit the memory available to the container

## Docker Hub
* Cloud service for storing and sharing Docker images. These are called "registries"
* [Caddy](https://hub.docker.com/u/caddy) has a namespace on the docker hub that shows how they have 2+ repositories available on here.
* Basically github for docker images

### Versioning (Tags)
* With tags if you push a docker image with a tag that already exists it will overwrite that, so if we push one with multiple tags we can use semantic versioning as well as keeping latest marked as the latest image
* Example:
```bash
docker build -t bootdotdev/awesomeimage:5.4.6 -t bootdotdev/awesomeimage:latest .
docker push bootdotdev/awesomeimage --all-tags
```
* In this we build it with a version tag and a latest tag then when we push it we push it with all tags, so on the repo site latest will always be at / near the top and always be the latest version

## Layer Caching & General Dockerfile Performance Tips
>[Video Talking about best docker practices](https://www.youtube.com/watch?v=t779DVjCKCs)
* When making a docker file layers will cache so you can utilize this to massively speed up your build process
* Cache Invalidation: If the cache get's invalidated it will have to re-cache the layers, for this there are some reasons a layer will get cache invalidated
	* Changes to the files you're copying: By changing a file here it will realize and re run this layer
	* Changes to the dockerfile instruction: If a change occurs in the instruction it will see and re-cache this layer
	* Changes to any previous layer: If any layer before this changed this might've change as there might be a dependency between these
* Due to the last one you can see that ordering of a dockerfile matters and isn't just a toss in and forget as if you have something that changes every time you push code near the top every layer will be forced to be re-cached and if one of those layers is an asset layer with multiple gigabytes of files you might result in a multiple minute imaging process instead of seconds
* Can use a `.dockerignore` to ignore unneeded folders / files for the build i.e: node modules
* Image Layers are immutable and contain only changes from the previous layer so earlier layers files are preserved so if you try to do an `install -> delete installer` it doesn't remove the images size as those files are still present albeit marked "not accessible"
	* So to get around this include all the removes into 1 layer command as this will shrink the size
* Example:
```bash
# One layer
RUN npm install --production && \
	npm run build && \
	npm cache clean --force && \
	rm -rf /root/.npm && \
	rm -rf node_modules

# Seperate Layers (Doesn't work)
RUN npm install --production
RUN npm run build
RUN npm cache clean --force
...
```

## Localhost Note
* When using localhost inside a docker container it refers to the container not the computer, just a note to keep track of

## Multi-stage builds
* Can separate out the runtime from the build-time so the build-time runs in a heavier environment with a bigger image (Compiler / tooling / NPM / etc) but this will produce a single binary at the end
* Afterwards you copy that binary over to a new runtime stage that uses a lighter image and then runs it in there
* Doing this allows you to massively shrink down the final image size as it goes from everything in one environment to throwing away the previous one when it is done resulting in just the end product
* Can use [slim](https://github.com/slimtoolkit/slim) to minify the docker image even further

## Go Builder & Runtime combos
* Builder:
	* `golang:1.22-alpine`
* Runner:
	* `gcr.io/distroless/base-debian12`
* 