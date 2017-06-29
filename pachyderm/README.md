Pachyderm-Minio Helm Chart
====================

This chart can be used to deploy Pachyderm backed by Minio, a lightweight, AWS S3 compatible object storage server.

Prerequisites Details
---------------------

-	Kubernetes
-	A dedicated namespace to install Pachyderm
-   PV provisioner support in the underlying infrastructure
-   Minio deployment on Kubernetes using Helm


Chart Details
-------------

This chart can do the following:

-	Deploy Pachyderm in any cloud infrastructure with PV provisioner support

How to install the chart
--------------------

You must install the chart with the release name previously assigned to the Minio chart:

```console
$ helm repo add pbcharts --url http://pharmb.io/pbcharts/
$ helm install --name pachyderm --set minio.releaseName=minio-release,accessKey= myaccesskey,secretKey=mysecretkey .
```

Heml chart settings
-------------------

The following tables lists the configurable parameters of the patroni chart and their default values.

| Parameter                | Description           | Default           |
|--------------------------|-----------------------|-------------------|
| `pachd.image.repository` | Container image name  | `pachyderm/pachd` |
| `pachd.image.tag`        | Container image tag   | `1.4.8`           |
| `pachd.worker.repository`| Worker image name     | `pachyderm/worker`|
| `pachd.worker.tag`       | Worker image tag      | `1.4.8`           |
| `pachd.image.pullPolicy` | Container pull policy | `IfNotPresent`    |
| `pachd.replicaCount`     | k8s petset replicas   | `1`               |
| `pachd.volume.volumeName`| Volume name           | `pachd_vol`       |
| `pachd.resources       ` | Request memory/cpu    | `1 & 5G`          |


Other parameters are also changeable. Please consult all available parameters in the `values.yaml` file.

Clean-up
-------

In order to remove everything, you can execute the following commands:

```console
$ helm list
$ helm delete <release-name>
```
