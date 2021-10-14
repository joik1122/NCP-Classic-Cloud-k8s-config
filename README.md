## k8s
> Creator: 한승진
> Date: 2021/10/14

## Description
* NCP Kubernetes service classic에 구축된 k8s 클러스터 관련 설정 파일 및 가이드 모음 리파지토리입니다.
* Kubernetes 1.12.7, Istio 1.5.9 기준으로 작성되었습니다.


## NCP 쿠버네티스 제어방법
* 1. NCP 콘솔 로그인
* 2. NKS 이동 https://console.ncloud.com/nks/clusters
* 3. 우측 "다운로드" 버튼을 눌러 설정파일 다운로드
* 4. 사용하는 CLI 도구에 맞추어 쿠버네티스 콘픽을 변수에 지정

- Powershell 환경변수
$KUBE_CONFIG=$HOME+"\Downloads\kubeconfig-xxxx.yaml"
$KC="--kubeconfig="+$KUBE_CONFIG

* 5. kubectl, istioctl 명령에 $KC 활용 (ex: kubectl get pod -n prod $KC)

