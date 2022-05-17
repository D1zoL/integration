cd .\integration\

rm .\dev\integration-dev-1.0.0.tgz
rm .\prod\integration-prod-1.0.0.tgz

helm package dev
helm package prod

mv integration-dev-1.0.0.tgz .\dev\
mv integration-prod-1.0.0.tgz .\prod\

cd ..

helm repo index integration/ --url https://d1zol.github.io/integration/
