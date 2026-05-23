


2026-02-23 Credit to Barrett B on this one
Tags: [[Software Engineering (SWE)]]
# Optimizing Docker Containers

## Layer Caching & General Dockerfile Performance Tips
>[Video Talking about best docker practices](https://www.youtube.com/watch?v=t779DVjCKCs)
* When making a docker file layers will cache so you can utilize this to massively speed up your build process
* Cache Invalidation: If the cache get's invalidated it will have to re-cache the layers, for this there are some reasons a layer will get cache invalidated
	* Changes to the files you're copying: By changing a file here it will realize and re run this layer
	* Changes to the dockerfile instruction: If a change occurs in the instruction it will see and re-cache this layer

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
* Can use [slim](https://github.com/slimtoolkit/slim) to minify the docker image even further****

# References
- 
