## This example deploys a base windows image and has a powershell command as it's entrypoint

## Best to use this example with ArgoCD
Reference: [prerequisites.md](../prerequisites.md)

## Create webserver from official base image if manual
`oc apply -f webserver.yaml` : This will create a Namespace, Service (with LB type), and Deployment (using a base image)