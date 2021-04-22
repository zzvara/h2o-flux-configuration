# H2O on Kubernetes

## Prerequisites

- Kubernetes version >1.17.
- Flux 1 already installed (using Helm) to Kubernetes
  from [Flux 1 installation using Helm](https://docs.fluxcd.io/en/latest/tutorials/get-started-helm/).
  Clone this repository and point Flux to your version.
- Flux Helm Operator already installed (using Helm) to Kubernetes
  from [Flux 1 Helm Operator installation using Helm](https://docs.fluxcd.io/projects/helm-operator/en/stable/).
- All services eat up about 25-60 GB of RAM.  

## About this repository

### `workloads/`

This directory contains exemplary Spark configuration, Traefik middleware
and OpenEBS' storage class. Not directly related to the project itself,
but may prove itself useful for inexperienced users.

### `releases/`

This directory contains services that must be installed to Kubernetes
and are direct dependencies of the H2O project. Your Kubernetes cluster
may have some of these already installed. Here, exemplary configuration
parameters are provided for these services.

### `projects/h2o/`

The project itself. Components:

- JFrog Artifactory for shared packages.
- Elasticsearch.
- Kibana.
- Default Spark configurations.

## Related repositories to publish to the JFrog Artifactory.

Scala code:

- https://github.com/zzvara/spark-disqus
- https://github.com/zzvara/spark-youtube

Docker images:

- https://hub.docker.com/repository/docker/zzvara/spark (Spark 3.1.1-SNAPSHOT,
  that is, the latest snapshot as of this commit.)
- https://hub.docker.com/repository/docker/zzvara/spark-youtube
- https://hub.docker.com/repository/docker/zzvara/spark-disqus

## How to run?

Once all services are running, publish `stube.yaml` (`SparkApplication`) to your cluster.
The latest application Docker image is already publish into Docker Hub.
Make sure to reconfigure the job itself, for this, see
`h2o-stube-spark-configuration.yaml`. (Especially access keys,
your configured Elasticsearch access, and so on.)

## Troubleshooting

- Refer to corresponding service troubleshooting for more information
  on how to set up and fix that service. For example, follow OpenVPN Git
  or repository URL you find in `openvpn.yaml`.