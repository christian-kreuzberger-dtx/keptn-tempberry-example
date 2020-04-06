# Keptn Tempberry

This is an example project for [Keptn](https://keptn.sh) for [Tempberry](https://github.com/ChristianKreuzberger/tempberry).

## Prerequesits

* A Kubernetes cluster (version 1.14 or 1.15)
* A working Keptn 0.6.1 installation

## Setup

1. Specify for project name in a variable
```console
PROJECT=tempberry
```

2. Create the project using Keptn Cli
```console
keptn create project $PROJECT --shipyard=shipyard.yaml
```

3. Onboard postgres and tempberry-backend
```console
keptn onboard service postgres --project=$PROJECT --chart=./postgres  --deployment-strategy=direct
keptn onboard service tempberry-backend --project=$PROJECT --chart=./tempberry-backend
```

4. And finally, send new artifacts for postgres and tempberry-backend
```console
keptn send event new-artifact --project=$PROJECT --service=postgres --image=postgres:10.4
keptn send event new-artifact --project=$PROJECT --service=tempberry-backend --image=ckreuzberger/tempberry-backend:0.1
```

## Cleanup

Make sure you have set the environment variable `$PROJECT` as specified in the Setup instructions above.

```console
keptn delete project $PROJECT
kubectl delete namespace $PROJECT-dev $PROJECT-hardening $PROJECT-production
```

## License

See [LICENSE](LICENSE).

