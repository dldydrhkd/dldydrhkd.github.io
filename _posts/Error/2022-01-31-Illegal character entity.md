---
title: 'com.ctc.wstx.exc.WstxParsingException: Illegal character entity: expansion character (code 0x8
at [row,col,system-id]:[3215,96,"file:/home/hadoop/hive-3.1.2/conf/hive-site.xml"]'
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-01-31 19:12:00
categories: [Error]
tags: [hive, hadoop, hive-site.xml]
math: true
mermaid: true
---

## Error 발생

- hive를 실행하였더니 다음과 같은 에러가 발생하였다.
    
    <img width="1145" alt="스크린샷_2022-01-31_오후_7 18 47" src="https://user-images.githubusercontent.com/48857296/160731546-afc39426-787e-4793-990f-771c2a633d84.png">
    

## Error 해결

- 에러에서 나온대로 hive-site.xml의 3215번째 줄을 보았더니 다음과 같이 이상한 문자가 있어 빼주었다.
    
    <img width="1143" alt="스크린샷_2022-01-31_오후_7 21 09" src="https://user-images.githubusercontent.com/48857296/160731557-1dc0e7ac-d08f-4b90-8eb5-6d3e6260cb05.png">
    
    - &#8; 을 빼주었다.
- 빼주고 다시 hive를 실행했더니 해결이 되었다.
