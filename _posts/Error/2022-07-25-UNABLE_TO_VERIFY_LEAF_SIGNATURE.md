---
title: "UNABLE_TO_VERIFY_LEAF_SIGNATURE"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-07-25 17:21:00
categories: [Error]
tags: [npm]
math: true
mermaid: true
---
## Error
- react 설치 중 다음과 같은 명령어를 실행했을 때 에러 발생

``` shell
npm install -g create-react-app
```
<img width="1047" alt="스크린샷 2022-08-01 오후 10 56 04" src="https://user-images.githubusercontent.com/48857296/182164854-208cf210-351b-47dc-9a71-19cec96e4adb.png">

## Error 해결
- ssl로 인해 설치가 막힌듯 하다.
- 다음 명령어를 사용하여 ssl 사용을 하지 않도록 변경한다.

``` shell
npm config set strict-ssl false
```

## 참고 사이트
[UNABLE_TO_VERIFY_LEAF_SIGNATURE 에러 발생시](https://yangyag.tistory.com/477)
