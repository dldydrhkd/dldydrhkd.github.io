---
title: "Python의 heapq와 PriorityQueue 차이"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2021-10-06 12:19:00
categories: [python]
tags: [python3, heapq, PriorityQueue]
math: true
mermaid: true
---

<aside>
💡 백준 문제를 풀다가 PriorityQueue는 시간초과가 뜨지만 heapq를 사용하면 시간초과가 뜨지 않았다. 왜 그럴까?
</aside>

## 해결

- 결론부터 말하자면 PriorityQueue는 스레드 안전 클래스이고 heapq는 스레드 안전을 보장하지 않는다.
- PriorityQueue는 스레드 안전을 위한 lock을 제공하기 때문에 잠금 오버 헤드가 있어 시간초과가 났던 것이다.
