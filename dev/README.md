helm install integration integration/ --values integration/values-local.yaml

helm template --dry-run --debug  --output-dir ./debug --namespace my-namespace integration ./integration

rm .\integration\integration-1.0.0.tgz

helm package integration

mv integration-1.0.0.tgz .\integration\

helm repo index integration/ --url https://d1zol.github.io/integration/

curl https://d1zol.github.io/integration/index.yaml


apiVersion: helm.openshift.io/v1beta1
kind: HelmChartRepository
metadata:
  name: integration
spec:
  name: integration
  connectionConfig:
    url: https://d1zol.github.io/integration/


oc adm policy add-scc-to-user anyuid -n oco-sandbox -z integration
