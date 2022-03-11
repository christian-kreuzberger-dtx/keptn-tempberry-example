# Keptn Tempberry

This is an example project for [Keptn](https://keptn.sh) for [Tempberry](https://github.com/ChristianKreuzberger/tempberry).

## Prerequesits

You need to have a Kubernetes cluster with a working Keptn 0.8.x installation (see https://keptn.sh/docs/quickstart/ steps 1 to 4)


## Status

- [x] Create chart for postgres
- [x] Create chart for tempberry backend
- [ ] Create chart for tempberry frontend
- [ ] Create superuser on installation
- [ ] Automatically run migrations (and roll them back if anything fails)
- [ ] Create JMeter tests for tempberry backend
- [ ] Run automated tests for installation in Keptn

## Setup

1. Specify for project name in a variable
```console
PROJECT=tempberry
```

2. Create the project using Keptn Cli
```console
keptn create project $PROJECT --shipyard=./shipyard.yaml
```

3. Onboard postgres and tempberry-backend
```console
keptn onboard service postgres --project=$PROJECT --chart=./postgres
keptn onboard service tempberry-backend --project=$PROJECT --chart=./tempberry-backend
```

4. Add SLO for hardening and tempberry-backend
```console
keptn add-resource --project=$PROJECT --stage=hardening --service=tempberry-backend --resource=slo.yaml --resourceUri=slo.yaml
```

4. And finally, send new artifacts for postgres and tempberry-backend
```console
keptn trigger delivery --project=$PROJECT --service=postgres --image=postgres:10.4 --sequence=delivery-direct
keptn trigger delivery --project=$PROJECT --service=tempberry-backend --image=ckreuzberger/tempberry-backend:0.1
```

## Cleanup

Make sure you have set the environment variable `$PROJECT` as specified in the Setup instructions above.

```console
keptn delete project $PROJECT
kubectl delete namespace $PROJECT-dev $PROJECT-hardening $PROJECT-production
```

## License

See [LICENSE](LICENSE).

