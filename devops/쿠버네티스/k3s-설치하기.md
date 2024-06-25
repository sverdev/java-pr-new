## K3s 설치하기

K8s의 CNI가 지속적으로 문제가 되어, k3s 환경으로 실습 해보기로 하였다.  
사실 온프로미스 환경에서 구축하는 경우도 적기도 하고 (많은 회사들이 클라우드 사용), 설치 부분의 트러블슈팅보다 사용 중 트러블슈팅 경험에 집중 하고 싶었다.

사실.. 허무할 정도로 간단하였다.

```
curl -sfL https://get.k3s.io | sh -
```

이 명령어만으로 자동으로 설치 해준다 ㅠㅠ 만세  
하지만 이렇게 간단하게 된다면 멋쟁이 홈랩이 아닌법, 노드를 가져올 수 없다는 에러와 함께 **couldn't get current server API group list** 가 출력 되었다. 구글에서 보니 아래 명령어로 해결이 가능 했다.

```
mkdir ~/.kube
sudo k3s kubectl config view --raw | tee ~/.kube/config
chmod 600 ~/.kube/config
```

첫번째 테스트 배포로 nginx를 선택 하였다. 아래의 명령어들로 진행이 가능하다 세상에.

```shell
kubectl create deployment deploy-nginx --image=nginx # 이미지로 deploy
kubectl expose deployment deploy-nginx --type=NodePort --port=80 # 포트를 열어줍니다.
kubectl get services # 해당 명령어를 통해 오픈된 포트를 확인 해주세요.
```

다음엔 멀티노드 구성을 해보겠다.
