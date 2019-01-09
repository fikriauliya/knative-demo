IP_ADDRESS := $(shell kubectl get svc knative-ingressgateway --namespace istio-system --output 'jsonpath={.status.loadBalancer.ingress[0].ip}')
HOST_URL := $(shell kubectl get ksvc helloworld-go  --output jsonpath='{.status.domain}')

deploy:
	kubectl apply -f service.yaml
curl:
	curl -H "Host: ${HOST_URL}" http://${IP_ADDRESS}
