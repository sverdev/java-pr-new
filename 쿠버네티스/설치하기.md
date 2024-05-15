## 쿠버네티스 설치하기

우선, 난 Proxmox 위의 Ubuntu 22.04 VM 여러개에서 **1 master - 2 slave** 형태로 구축 하여 학습 하기로 하였다. 노드의 수는 추후 추가가 가능하니, 먼저 구현을 해보도록 하였다.

블로그들의 글을 찾다가, 우연히 명령어를 리스트 형태로 정리해둔걸 찾았고, 실행 해보니 **Package repository deprecation** 으로 인하여 정상적인 이용이 불가능 하여 새 레포지토리로 구문을 일부 변경 해주었다.

- 정리해둔 파일은 내 깃허브 레포에 있으니 해당 스크립트를 사용해도 좋을 듯 하다.  
   ~~다만 내 스크립트는 설치 과정만을 담고 있고 설정은 따로 해줘야 한다. 아래에서 게속 보자~~

먼저, master-node에서 Kubernetes init 을 해줘야 한다.

```
sudo kubeadm init
```

후, 정상적으로 실행 되었다면

```
Then you can join any number of worker nodes by running the following on each as root:

kubeadm join (아이피):(포트) --token (값).(값) \
        --discovery-token-ca-cert-hash sha256:(값)
```

이런식으로 나올텐데 아래의 join 명령어를 slave-node에서 실행하면 된다.  
까먹었는데 master-node에서 아래의 명령어도 입력 해주어야 한다. (root 권한에서만 작동한다.)

```
export KUBECONFIG=/etc/kubernetes/admin.conf
```

노드 등록 후,  
아래의 명령어를 쳤을때 각 노드들의 STATUS가 NotReady로 나오면 정상적으로 노드가 등록 된건다.

```
kubectl get nodes
```
