IP_ADDRESS := $(shell kubectl get svc knative-ingressgateway --namespace istio-system --output 'jsonpath={.status.loadBalancer.ingress[0].ip}')
HOST_URL := $(shell kubectl get ksvc autoscale --output jsonpath='{.status.domain}')

deploy:
	kubectl apply -f service.yaml
curl:
	curl -H "Host: ${HOST_URL}" http://${IP_ADDRESS}
load:
	~/go/bin/hey -z 5s -c 50 -host "${HOST_URL}" "http://${IP_ADDRESS}?sleep=100&prime=10000&bloat=5" 
