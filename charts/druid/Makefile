.PHONY: install add-repo

install:
	helm upgrade --install --namespace "druid" druid . -f docker-desktop-cluster.yaml,values.yaml

add-repo:
	helm repo add incubator https://kubernetes-charts-incubator.storage.googleapis.com/
	helm repo update