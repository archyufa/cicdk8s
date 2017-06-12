# Create docker container of "Happy Birthday K8s" application.
This Demo App was written in "go" and supposed to be pushed to docker registry.
K8s will fetch our "Happy Birthday K8s" application. from docker Registry
and deploy pod, service, deployment. Farther we going to test how Replicaton
Controller puts cluster to desired state. We will than Scale Application and
perform Rolling Update of new version of the App.

1. Create Docker image:

 Build container:

```
cd ../demo3
chmod +x ./build.sh
./build.sh
```

 Push to docker registry:

```
docker build -t archyufa/webk8sbirthday:1.0.4 .
docker push archyufa/webk8sbirthday:1.0.4
```

2. Create Deployment and Service:

`kubectl create -f kdemo/`


## Installing with Helm Chart

To install the chart with the release name `my-release`:

```bash
$ helm install charts/simple-app-0.1.0.tgz
```

## Configuration

The following tables lists the configurable parameters of the Spark chart and their default values.

### Simple-app

|       Parameter       |           Description            |                         Default                          |
|-----------------------|----------------------------------|----------------------------------------------------------|
| `Name`            | app name                         | `simple-app`                                                |
| `Image`           | Container image name             | `archyufa/webk8sbirthday`                               |
| `ImageTag`        | Container image tag              | ` 1.0.1`                                                     |
| `ImagePullPolicy` | Container pull policy            | `Always`                                                     |
| `Replicas`        | k8s deployment replicas          | `3`                                                          |
| `Cpu`             | container requested cpu          | `10m`                                                        |
| `Memory`          | container requested memory       | `128Mi`                                                      |
| `ServiceType`     | k8s service type                 | `NodePort`                                               |
| `ServicePort`     | k8s service port                 | `80`                                                         |
| `ContainerPort`   | Container listening port         | `8080`                                                       |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
$ helm install --name my-release -f values.yaml charts/simple-app-0.1.0.tgz
```

> **Tip**: You can use the default [values.yaml](values.yaml)
