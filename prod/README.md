helm install integration integration/ --values integration/values-local.yaml

helm template --dry-run --debug  --output-dir ./debug-prod --namespace my-namespace prod ./prod

