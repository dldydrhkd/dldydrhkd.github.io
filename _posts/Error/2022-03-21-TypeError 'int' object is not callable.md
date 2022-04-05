---
title: "TypeError: 'int' object is not callable"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-03-21 18:35:00
categories: [Error]
tags: [len, python3]
math: true
mermaid: true
---

## Error

- python으로 알고리즘 문제를 풀던 중 len()함수가 도저히 먹히지가 않고 다음과 같은 에러가 계속 나왔다.
    
    ```python
    Traceback (most recent call last):
      File "/Users/lyk/Documents/CPP/t.py", line 49, in <module>
        if(check(mid,l,k)):
      File "/Users/lyk/Documents/CPP/t.py", line 14, in check
        print(len(temp_l))
    TypeError: 'int' object is not callable
    ```
    

## Error 해결

- len이라는 변수를 사용해서 생긴 에러였다.
- 이미 정해져 있는 함수 이름은 변수 이름으로 사용하지 말자.
