# jaeger stack helm 인스톨 가이드

필요한 사전 스택
ISTIO
Elastic Search

1. repository 추가
helm repo add jaegertracing https://jaegertracing.github.io/helm-charts

2. 네임스페이스 생성
kubectl create namespace tracing

3. 헬름 배포
helm install jaeger jaegertracing/jaeger --set provisionDataStore.cassandra=false --set storage.type=elasticsearch --set storage.elasticsearch.host=elasticsearch.logging.svc.cluster.local --set storage.elasticsearch.port=9200 --set collector.service.zipkin.port=9411 -n tracing

4. ISTIO 에드온 활성화 작업
istioctl manifest apply --kubeconfig=$KUBE_CONFIG --set profile=default --set 'values.gateways.istio-ingressgateway.serviceAnnotations.service\.beta\.kubernetes\.io/ncloud-load-balancer-internal=true' --set addonComponents.grafana.enabled=true --set addonComponents.kiali.enabled=true --set "values.kiali.dashboard.jaegerURL=http://jaeger-query.tracing" --set "values.kiali.dashboard.jaegerInClusterURL=http://jaeger-query.tracing" --set values.global.tracer.zipkin.address=jaeger-collector.tracing:9411 --set values.pilot.traceSampling=5


레퍼런스 
https://github.com/jaegertracing/helm-charts/tree/master/charts/jaeger
구축 당시 Repository Tag : Master jaeger-0.34.1


