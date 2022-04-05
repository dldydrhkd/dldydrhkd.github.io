---
title: 'unable to open swap file “Filename” for recovery impossible'
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-02-26 18:57:00
categories: [Error]
tags: [vi, vim, swap file]
math: true
mermaid: true
---

## Error

- python 파일을 고치기 위해 vim으로 열었지만 이전과는 다르게 다음과 같이 에러가 나면서 이상해졌다.
    
    <img width="759" alt="스크린샷_2022-02-26_오후_6 57 09" src="https://user-images.githubusercontent.com/48857296/161663214-fb9846b6-128d-481e-9b0f-7e1f355f7154.png">
    

## Error 해결

- 메모리 공간이 부족하거나 알 수 없는 이유로 인해서 편집 이력이 있었던 파일의 스왑(SWAP) 파일을 열지 못하여 발생하는 문제이다.
- 아니나 다를까 `df -h` 명령으로 메모리를 확인을 해보니 디스크 용량이 100%가 차 있는것을 볼 수 있었다.
- 파일을 지우거나 디스크 용량을 늘려주어 해결하였다.
