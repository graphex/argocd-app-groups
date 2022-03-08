# argocd-app-groups

This repo builds and publishes the infra-argocd-appgroup helm chart.
This chart is a somewhat opinionated, app-of-apps implementation for ArgoCD.
Simple and flexible definitions of apps is the primary goal,
so the project follows these general guidelines:
* AppGroups and the Apps they create should all belong to the same AppProject
* One AppGroup per environment (dev/stage/prod)
* Environment prefix should be added to both namespace and app names
* By default, values files are configured to be:
  * values.yaml
  * values-{environment}.yaml

## To test templating (from the `src/main/helm` directory):

```helm template . -f _test-values.yaml --debug```

See the `_test-values.yaml` for examples of advanced feature usage

## Publishing a new version (from the root directory)
TODO: Automate this
```
helm package helm/ --destination charts
helm repo index charts/
git subtree push --prefix charts origin gh-pages
```