helm install integration integration/ --values integration/values-local.yaml

helm template --dry-run --debug  --output-dir ./debug-dev --namespace my-namespace dev ./dev
