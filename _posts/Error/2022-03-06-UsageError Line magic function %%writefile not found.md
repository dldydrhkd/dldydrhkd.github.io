---
title: "UsageError: Line magic function %%writefile not found."
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-03-06 23:49:00
categories: [Error]
tags: [magic function, python3, writefile]
math: true
mermaid: true
---

## Error

```python
# jupyter notebook 상에서 파일 생성 명령어, 이미 있다면 덮어씌운다.
%%writefile fibo.py

def fib(n):
    a, b = 0, 1
    
    while b<n:            # 조건이 true인 경우에만 실행되는 반복문
        print(b, end=' ')
        a, b = b, a+b
```

- 위와 같은 코드를 작성하였더니 다음과 같은 에러가 발생하였다.
    
    <img width="806" alt="스크린샷_2022-03-07_오전_10 32 46" src="https://user-images.githubusercontent.com/48857296/161663638-f37f9d12-2fe3-4e0e-81db-a7791af3e6ff.png">
    

## Error 해결

- magic command %%writefile은 jupyter notebook cell의 첫번째 줄에 작성해야 한다.
- 다음과 같이 수정하였더니 정상적으로 동작했다.
    
    ```python
    %%writefile fibo.py
    # jupyter notebook 상에서 파일 생성 명령어, 이미 있다면 덮어씌운다.
    
    def fib(n):
        a, b = 0, 1
        
        while b<n:            # 조건이 true인 경우에만 실행되는 반복문
            print(b, end=' ')
            a, b = b, a+b
    ```
    

## 참고 사이트

[python jupyter magic %%writefile returns SyntaxError: invalid syntax](https://stackoverflow.com/questions/52255582/python-jupyter-magic-writefile-returns-syntaxerror-invalid-syntax)
