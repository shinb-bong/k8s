결과가 ReplicaSet과 비슷해 보이지만 
Deploymemt 는 Pod를 새로운 이미지로 업데이트할때 발휘

> Deployment는 새로운 이미지로 업데이트하기 위해 ReplicaSet을 이용합니다. 버전을 업데이트하면 새로운 ReplicaSet을 생성하고 해당 ReplicaSet이 새로운 버전의 Pod을 생성합니다.
`kubectl describe deploy/echo-deploy`

1. Deployment Controller는 Deployment조건을 감시하면서 현재 상태와 원하는 상태가 다른 것을 체크

2. Deployment Controller가 원하는 상태가 되도록 ReplicaSet 설정

3. ReplicaSet Controller는 ReplicaSet조건을 감시하면서 현재 상태와 원하는 상태가 다른 것을 체크

4. ReplicaSet Controller가 원하는 상태가 되도록 Pod을 생성하거나 제거

5. Scheduler는 API서버를 감시하면서 할당되지 않은unassigned Pod이 있는지 체크

6. Scheduler는 할당되지 않은 새로운 Pod을 감지하고 적절한 노드node에 배치

7. 이후 노드는 기존대로 동작


버전관리
---

- 히스토리 확인

kubectl rollout history deploy/echo-deploy

- 히스토리 상세 확인

kubectl rollout history deploy/echo-deploy --revision=1

- 바로 전으로 롤백

kubectl rollout undo deploy/echo-deploy

- 특정 버전으로 롤백

kubectl rollout undo deploy/echo-deploy --to-revision=2


Deployment 다양한 방식의 배포 전략이 있습니다. 여기선 롤링업데이트RollingUpdate 방식을 사용할 때 동시에 업데이트하는 Pod의 개수를 변경해보겠습니다.