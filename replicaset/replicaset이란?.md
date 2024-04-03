Pod을 단독으로 만들면 Pod에 어떤 문제(서버가 죽어서 Pod이 사라졌다던가)가 생겼을 때 자동으로 복구되지 않습니다. 이러한 Pod을 정해진 수만큼 복제하고 관리하는 것이 ReplicaSet입니다.
---

ReplicaSet은 label을 체크해서 원하는 수의 Pod이 없으면 새로운 Pod을 생성합니다. 이를 설정으로 표현하면 다음과 같습니다.

---
ReplicaSet은 ReplicaSet Controller가 관리하고 Pod의 할당은 여전히 Scheduler가 관리합니다. 

ReplicaSet은 원하는 개수의 Pod을 유지하는 역할을 담당합니다. label을 이용하여 Pod을 체크하기 때문에 label이 겹치지 않게 신경써서 정의해야 합니다.

실전에서 ReplicaSet을 단독으로 쓰는 경우는 거의 없습니다. 바로 다음에서 배울 Deployment가 ReplicaSet을 이용하고 주로 Deployment를 사용합니다.

