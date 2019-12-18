# Keptn Tempberry

## Setup

```console
keptn create project cktempberry --shipyard=shipyard.yaml

keptn onboard service tempberry-db --project=cktempberry --chart=./tempberry-db  --deployment-strategy=direct
keptn onboard service tempberry --project=cktempberry --chart=./tempberry
```

send new artifacts

```console
keptn send event new-artifact --project=cktempberry --service=tempberry-db --image=postgres:10.4
keptn send event new-artifact --project=cktempberry --service=tempberry --image=ckreuzberger/tempberry-backend:master
```