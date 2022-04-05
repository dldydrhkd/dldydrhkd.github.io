---
title: "백준 python RecursionError"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-02-01 18:10:00
categories: [Error]
tags: [RecursionError, python3, 백준]
math: true
mermaid: true
---

## Error

- 백준 문제를 풀던 도중 recursion error가 발생하였다.
    
    <img width="1133" alt="스크린샷_2022-04-03_오후_9 08 01" src="https://user-images.githubusercontent.com/48857296/161669329-5834da07-de8e-4620-bc56-9554ac9b063b.png">
    

## Error 해결

- 백준의 경우 python 재귀함수의 호출 스택이 1000까지로 설정되어 있다.
- 다음을 코드에 추가 시켜 함수 스택 limit을 조절할 수 있다.
    
    ```python
    import sys
    
    sys.setrecursionlimit(10**6)
    ```
    

## 참고 사이트

[런타임 에러 (RecursionError)](https://help.acmicpc.net/judge/rte/RecursionError)
