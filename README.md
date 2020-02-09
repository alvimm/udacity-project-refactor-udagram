# Udacity
## Cloud developer - Refactor Udagram into microservices

### Running locally with Docker

1. You should define these envinronment variables locally:
  - POSTGRESS_USERNAME
  - POSTGRESS_PASSWORD
  - POSTGRESS_DB
  - POSTGRESS_HOST
  - AWS_REGION
  - AWS_PROFILE
  - AWS_BUCKET
  - JWT_SECRET

2. Build images with:
`docker-compose -f ./udacity-c3-deployment/docker/docker-compose-build.yaml build`
3. Then run with:
`docker-compose -f ./udacity-c3-deployment/docker/docker-compose.yaml up`
4. See the app in `localhost:8100`.

### Running with Kubernetes

#### Configure cluster

In order to run this project properly with Kubernetes, you should previously configure your
cluster. I recommend using Kubeone for this and follow [these instructions](https://github.com/kubermatic/kubeone/blob/master/docs/quickstart-aws.md).

#### Set up envinronment variables

Set up the envinroment variables properly in
`./udacity-c3-deployment/k8s/env-configmap.yaml`.

Then you should set your secrets in `env-secrets.yaml` and `aws-secret.yaml`.
These secrets should be stored as base64 strings. You could use `echo yourstring | base64` to
convert a string to base64 encoded or `base64 -in /path/to/file` to convert a file.

#### Load environment variables, deployments and services

Execute `kubectl apply -f ./udacity-c3-deployment/k8s/.` to load all configmaps, secrets,
deployments and services.

You could run `kubectl get all` to check if everything is running.

#### Port forwarding

To connect your localhost ports with the containers execute:
```
kubectl port-forward service/frontend 8100:8100
kubectl port-forward service/reverseproxy 8080:8080
```

See the app running in `localhost:8100`.

Mauricio Alvim :smile: