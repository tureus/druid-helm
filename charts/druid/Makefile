.PHONY: install add-repo

template:
	helm template --namespace=druid druid .

install:
	kubectl config use-context docker-desktop
	#helm upgrade --install --namespace "druid" druid . -f values.yaml,docker-desktop-cluster.yaml
	helm upgrade --install --namespace=druid druid-broker      . -f values.yaml,docker-desktop-cluster.yaml --set=component=broker      --set=port=8082
	helm upgrade --install --namespace=druid druid-coordinator . -f values.yaml,docker-desktop-cluster.yaml --set=component=coordinator --set=port=8081
	helm upgrade --install --namespace=druid druid-overlord    . -f values.yaml,docker-desktop-cluster.yaml --set=component=overlord    --set=port=8081
	helm upgrade --install --namespace=druid druid-router      . -f values.yaml,docker-desktop-cluster.yaml --set=component=router      --set=port=8888
	helm upgrade --install --namespace=druid druid-historical  . -f values.yaml,docker-desktop-cluster.yaml --set=component=historical  --set=port=8083
	helm upgrade --install --namespace=druid druid-indexer     . -f values.yaml,docker-desktop-cluster.yaml --set=component=indexer     --set=port=8091

install-zk:
	helm upgrade --install --namespace=druid zookeeper         charts/zookeeper --set=env.ZK_HEAP_SIZE=512M --set=persistence.enabled=true

install-mysql:
	helm upgrade --install --namespace=druid mysql             charts/mysql -f mysql-values.yaml

add-repo:
	helm repo add incubator https://kubernetes-charts-incubator.storage.googleapis.com/
	helm repo update