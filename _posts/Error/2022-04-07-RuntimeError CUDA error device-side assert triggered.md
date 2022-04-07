---
title: "RuntimeError: CUDA error: device-side assert triggered"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-04-07 10:07:00
categories: [Error]
tags: [CUDA, colab, kobert, nlp]
math: true
mermaid: true
---
## Error

- kobert를 실행시키던 도중 다음과 같은 에러가 발생하였다.
    
    <img width="453" alt="스크린샷_2022-04-07_오후_3 42 34" src="https://user-images.githubusercontent.com/48857296/162196187-13f485cd-c3c2-4b86-b805-866349131320.png">
    

## Error 해결

- 이런 경우 보통 차원 수가 맞지 않아 발생하는 에러라고 한다.
- 아니나 다를까 9개로 분류를 해야하는데 3으로 되어 있어 고쳤더니 에러가 바로 해결되었다.

## 참고 사이트

[[PyTorch 오류 해결] RuntimeError: CUDA error: device-side assert triggered](https://ndb796.tistory.com/509)
