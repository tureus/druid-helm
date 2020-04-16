install:
	kubectl config use-context ids-dev
	helm upgrade --install --namespace=druid druid-broker      ../../ -f ../../values.yaml,ids-dev.yaml --set=component=broker      --set=port=8082
	helm upgrade --install --namespace=druid druid-coordinator ../../ -f ../../values.yaml,ids-dev.yaml --set=component=coordinator --set=port=8081
	helm upgrade --install --namespace=druid druid-overlord    ../../ -f ../../values.yaml,ids-dev.yaml --set=component=overlord    --set=port=8081
	helm upgrade --install --namespace=druid druid-router      ../../ -f ../../values.yaml,ids-dev.yaml --set=component=router      --set=port=8888
	helm upgrade --install --namespace=druid druid-historical  ../../ -f ../../values.yaml,ids-dev.yaml --set=component=historical  --set=port=8083
	helm upgrade --install --namespace=druid druid-indexer     ../../ -f ../../values.yaml,ids-dev.yaml --set=component=indexer     --set=port=8091

template:
	helm template --namespace=druid druid-broker ../../ -f ../../values.yaml,ids-dev.yaml --set=component=broker --set=port=8082