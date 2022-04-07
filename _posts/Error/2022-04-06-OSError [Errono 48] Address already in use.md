---
title: "OSError: [Errono 48] Address already in use"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-04-06 20:43:00
categories: [Error]
tags: [flask]
math: true
mermaid: true
---
## Error

- Flask를 실행했더니 다음과 같이 이미 사용되고 있다고 에러가 발생하였다.
    
    <img width="828" alt="스크린샷_2022-04-07_오전_12 58 16" src="https://user-images.githubusercontent.com/48857296/162194334-b3f9b9e6-eda5-47a2-9e72-d390d895a8da.png">
    

## Error 해결

- 다음 명령어로 핸재 돌아가고 있는 프로세스를 확인한다.
    
    ```bash
    ps -ef | grep python
    ```
    
- 프로세스의 pid를 확인하고 프로세스를 죽인다.
    
    ```bash
    kill -9 [pid]
    ```
