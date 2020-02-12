---
layout: post
title: 내가 보려고 만든 AWS 칱 싵
---

예상에 없던 AWS로 서비스를 만들다보니 코드 짜는거보다 적절스한 커맨드 찾는데에 시간 더 많이 걸려서 여기에 남기고 나중에 복붙하려고 만들었음 낄낄

# Cognito

## Configure
* aws cli로 user pools에 무슨 짓을 하고싶다면 App clients 만들때 Generate client secret를 꼭 체크 해제 하거라.. 이거땜시 Unable to verify secret hash for client 계속 봤네

## Command
* 테스트 하려면 id_key 필요 > 앗 테스트 계정 비번 까먹음;
```console
aws cognito-idp forgot-password --client-id {CLIENT_ID} --username {USERNAME}
```


* 인증코드 받아서 비밀번호 변경
```console
aws cognito-idp confirm-forgot-password --client-id {CLIENT_ID} --username={USERNAME} --password {NEW_PASSWORD} --confirmation-code {CODE}
```

* 아이디, 비밀번호 알았으니 auth 정보 가져오기
```console
aws cognito-idp admin-initiate-auth --user-pool-id=eu-central-1_{USER_POOL_ID} --client-id={CLIENT_ID} --auth-flow=ADMIN_NO_SRP_AUTH --auth-parameters=USERNAME={USERNAME},PASSWORD={PASSWORD}
```

---






 

