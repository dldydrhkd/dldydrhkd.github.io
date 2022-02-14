---
title: Python의 immutable 객체와 mutable 객체
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2021-09-28 17:06:00
categories: [Language, Python]
tags: [python,variable]
math: true
mermaid: true
---

💡 `[[0]*3]*3`과 `[[0]*3 for _ in range(3)]`의 차이점이 무엇일까?

# 궁금증

- 코드 둘 다 [[0,0,0],[0,0,0],[0,0,0]]을 만든다. 그렇다면 어떤 차이가 있을까?
- [0][0]의 숫자를 1로 바꿔보자
- 생각대로라면 [[1,0,0],[0,0,0],[0,0,0]]이 나와야 한다. 하지만 `[[0]*3]*3` 의 코드로 작성한 경우 [[1,0,0],[1,0,0],[1,0,0]] 이 된다.
- 이유를 알아보자

# 해결

- python의 변수는 크게 immutable 객체와 mutable객체 두 가지로 나뉜다.
    - mutable
        - Lists
        - Sets
        - Dictionaries
        - User-Defined Classes
    - immutable
        - Numbers(Integer, Rational, Float, Decimal, Complex & Booleans)
        - Strings
        - Tuples
        - Frozen Sets
        - User-Defined Classes
- 쉽게 설명하면 mutable은 선언후 변하는것이고 immutable은 선언 후 변하지 않는 것이다.
- python의 `*` 의 경우 복사를 의미한다. 복사할 때 mutable인 경우는 얕은 복사를 하고 immutable일 때는 깊은 복사를 한다
- `[0]*3`은 0이 mutable이므로 깊은 복사가 일어나 값만 복사를 한다. 그렇기 때문에 주소가 각기 다른 [0,0,0] 배열이 만들어진다.
- 만들어진 [0,0,0]을 `*` 연산으로 3을 곱하면 [0,0,0]이 3개가 만들어지는데 결국 다 같은 주소를 갖는 배열이 3개가 되는것이다.
- python의 모든 객체는 id 함수와 is 연산자가 제공되니 이를 이용하여 직접 코딩으로 확인해보자

# 참고

[Python 개념 정리 - 객체란](https://webnautes.tistory.com/1181)

[Understanding Mutable and Immutable in Python - Great Learning](https://www.mygreatlearning.com/blog/understanding-mutable-and-immutable-in-python/)
