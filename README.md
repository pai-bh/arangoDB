# arangoDB
- 작업환경 : m1 mac


---

### 1. Dokcer images pull 및 Arangodb container가동
- m1에 익숙치않아서 pull을 통해 이미지 가져오려고하면 `no matching manifest for linux/arm64 in the manifest list entries` 에러가 발생함. 이를 해결하지 못하고 구글링을통해 아래와 같은 답변을 얻어서 pull 없이 바로 run 을 통해 이미지 다운로드받음
- 초기비밀번호는 __password__ 로 진행하도록 하겠습니다.
```shell
$ docker run -e ARANGO_ROOT_PASSWORD=password -p 8529:8529 -d --platform linux/x86_64/v8 --name arangodb arangodb
```

근데 정작 정상가동은 안되네..  
다른 이미지 사용하기로함 `arangodb/arangodb:3.9.0-noavx`

```shell
$ docker pull arangodb/arangodb:3.9.0-noavx

```
# 이미지 불러오기
```
$ docker run \
  -e ARANGO_ROOT_PASSWORD=password \
  -p 8529:8529 \
  -d \
  --name arangodb \
  arangodb/arangodb:3.9.0-noavx
```

 <img width="1405" alt="image" src="https://user-images.githubusercontent.com/83193687/171561553-acede20c-e895-4d20-8002-0cea2ed34328.png">

위처럼 되긴 하는데, m1이라서 다음과 같은 경고뜸
`WARNING: The requested image's platform (linux/amd64) does not match the detected host platform (linux/arm64/v8) and no specific platform was requested`

초기 아이디 셋팅
```
ID : root
PW : password
```
