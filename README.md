# Udacity
## Cloud developer - Refactor Udagram into microservices

### Running locally with Docker

You should previously define these envinronment variables locally:
  - POSTGRESS_USERNAME
  - POSTGRESS_PASSWORD
  - POSTGRESS_DB
  - POSTGRESS_HOST
  - AWS_REGION
  - AWS_PROFILE
  - AWS_BUCKET
  - JWT_SECRET

Build images with:
`docker-compose -f ./udacity-c3-deployment/docker/docker-compose-build.yaml build`
Then run with:
`docker-compose -f ./udacity-c3-deployment/docker/docker-compose.yaml up`

### Running with Kubernetes

#### Set up envinronment variables

First you need to set up the envinroment variables properly in
`./udacity-c3-deployment/k8s/env-configmap.yaml`.

Then you should set your secrets in `env-secrets.yaml` and `aws-secret.yaml`.
These secrets should be stored as base64 strings. You could use `echo yourstring | base64` to
convert a string to base64 encoded or `base64 -in /path/to/file` to convert a file.

#### Load environment variables, deployments and services

T

Mauricio Alvim :smile: