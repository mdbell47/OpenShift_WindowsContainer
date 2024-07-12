## This example built image, pushed to registry

Reference: [prerequisites.md](../prerequisites.md)

## Build image and push to registry
`docker build -t yourTag .` 

`docker tag yourTag yourregistry.com/user/yourimage:tag`

`docker push yourregistry.com/user/yourimage:tag`