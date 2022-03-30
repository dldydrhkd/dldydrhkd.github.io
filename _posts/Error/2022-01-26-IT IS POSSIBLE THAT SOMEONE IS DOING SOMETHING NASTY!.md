---
title: IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-01-26 00:31:00
categories: [Error]
tags: [ssh, linux]
math: true
mermaid: true
---

## 에러 발생

- ssh 원격 접속을 하려 했는데 다음과 같은 에러가 발생했다.
    
    <img width="646" alt="스크린샷_2022-01-26_오전_12 32 06" src="https://user-images.githubusercontent.com/48857296/160727956-97f904a5-15c2-4ab1-bcc5-f26410e94c1a.png">

    

## 문제 해결

- 문제는 접속 시 man-in-the-middle attack이라고 판단하여 보안상 문제가 발생할 수 있어 막는거 같다.
- 다음과 같은 명령어를 실행하면 문제 없이 원격접속이 가능하다.
    
    ```bash
    rm -rf ~/.ssh/known_hosts
    ```
