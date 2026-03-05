
2026-02-08

Tags: [[Software Development]]
# Docker Basics

```Bash
# sets all containers up
docker-compose up

# Tear it down and rebuild from scratch, without cache too
docker compose down -v && docker compose build --no-cache && docker compose up -d

# Rebuild just one container from scratch
docker-compose build --no-cache container 

# Get a shell in a container
docker exec container sh

# SSH Into a database directly
docker exec -it postgres psql -U user -d db 

# Build and run a single container without tags, removes when done
docker run --rm -it $(docker build -q .) /bin/bash
```

## Registries
The docker registries is a storage and distribution system for docker images that lets you find and share docker images. One of the biggest ones is Docker Hub.

**Official images** have been reviewed and serves as a guarantee that best practices were followed.
# References
- 

