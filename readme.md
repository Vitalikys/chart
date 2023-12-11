## Helm Chart Repository for Kubernetes

### How to use
```shell
helm repo add schedule-app  https://vitalikys.github.io/chart/
```

Get list of available versions:
```shell
helm search repo schedule-app
```

### How to create new version
Generate index.yaml:
```shell
helm repo index .
```


make package to .tgz zip
```shell
helm package $(pwd)/ -d $(pwd)/
```

```shell
helm package .
```

Successfully packaged chart and saved it to: ../app-0.1.0.tgz

### How to store on S3 bucket
```shell
helm s3 init s3://vit-helm.io/charts
helm repo add schedule s3://vit-helm.io/charts
helm repo list

helm s3 push --relative ./schedule-app-0.1.0.tgz schedule
helm search repo schedule
```
