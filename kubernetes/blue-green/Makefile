IP_ADDRESS := $(shell kubectl get svc knative-ingressgateway --namespace istio-system --output 'jsonpath={.status.loadBalancer.ingress[0].ip}')
HOST_URL := blue-green-demo.default.example.com

deploy:
	kubectl apply -f blue-green-demo-config.yaml
	kubectl apply -f blue-green-demo-route.yaml
curl:
	curl -H "Host: ${HOST_URL}" http://${IP_ADDRESS}
curl_v1:
	curl -H "Host: v1.${HOST_URL}" http://${IP_ADDRESS}
curl_v2:
	curl -H "Host: v2.${HOST_URL}" http://${IP_ADDRESS}

