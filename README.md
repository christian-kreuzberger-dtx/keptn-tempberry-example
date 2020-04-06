# Keptn Tempberry

## Setup

```console
keptn create project ck-tempberry --shipyard=shipyard.yaml

keptn onboard service postgres --project=ck-tempberry --chart=./postgres  --deployment-strategy=direct
keptn onboard service tempberry-backend --project=ck-tempberry --chart=./tempberry-backend
```

send new artifacts

```console
keptn send event new-artifact --project=ck-tempberry --service=postgres --image=postgres:10.4
keptn send event new-artifact --project=ck-tempberry --service=tempberry-backend --image=ckreuzberger/tempberry-backend:master
```