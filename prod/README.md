helm install integration integration/ --values integration/values-local.yaml

helm template --dry-run --debug  --output-dir ./debug --namespace my-namespace prod ./prod

rm .\prod\prod-1.0.0.tgz

helm package prod

mv integration-prod-1.0.0.tgz .\prod\

helm repo index prod/ --url https://d1zol.github.io/integration/

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
