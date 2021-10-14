## Deprecated
> (*중요)Nginx Ingress controller는, Istio를 사용하면서 더이상 사용하지 않습니다.
> 해당 문서는 보관을 위해 유지합니다.


## NCP Private LoadBalancer와 Ingress Controller 서비스 생성을 위한 Yaml파일입니다.
> 관련 설명서는 https://docs.ncloud.com/ko/nks/nks-1-4.html 에서 확인 가능합니다.

## 1. IngressController 배포 (택 1)
> kubectl --kubeconfig $KUBE_CONFIG apply -f ./mandatory.yaml
> kubectl --kubeconfig $KUBE_CONFIG apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/2de5a893aa15f14102d714e918b0045b960ad1a5/deploy/static/mandatory.yaml

## 2. Ingress Service 생성
> kubectl --kubeconfig $KUBE_CONFIG apply -f ./cloud-generic.yaml

## 3. 로드밸런서 생성여부 실시간 확인
> kubectl --kubeconfig $KUBE_CONFIG get service -n ingress-nginx --watch

