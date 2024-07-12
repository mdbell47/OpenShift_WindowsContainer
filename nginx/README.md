## This example built image, pushed to registry, and deployed using oc cli
Reference: [prerequisites.md](../prerequisites.md)

## Build image and push to registry
`docker build -t yourTag .` 

`docker tag yourTag yourregistry.com/user/yourimage:tag`

`docker push yourregistry.com/user/yourimage:tag`

## Create webserver from official base image if manual
`oc apply -f nginx_manifest.yaml` : This will create a Namespace, Service (with LB type), and Deployment (using a base image)