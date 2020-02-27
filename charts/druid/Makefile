.PHONY: install add-repo

template:
	helm template --namespace=druid druid .

install:
	kubectl config use-context docker-desktop
	helm upgrade --install --namespace "druid" druid . -f values.yaml,docker-desktop-cluster.yaml --wait

add-repo:
	helm repo add incubator https://kubernetes-charts-incubator.storage.googleapis.com/
	helm repo update