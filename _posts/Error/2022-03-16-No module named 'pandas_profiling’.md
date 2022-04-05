---
title: "No module named 'pandas_profiling’"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-03-16 18:09:00
categories: [Error]
tags: [pandas, pandas_profiling]
math: true
mermaid: true
---

## Error

- env01이라는 내가 만든 conda 가상환경에서 `pip install pandas-profiling` 명령어로 pandas-profiling으로 설치 후 jupyter notebook에서 `pandas_profiling` 을 import 하였지만 다음과 같은 에러가 발생하였다.
    
    <img width="875" alt="스크린샷_2022-03-16_오후_6 41 49" src="https://user-images.githubusercontent.com/48857296/161665582-ac4892f9-7b80-4fa6-aa49-73dd597fd288.png">
    

## Error 해결

- env01은 python 3.6 버전이었다. 아무리 삭제하고 재설치를 해도 되지 않아 깔끔하게 새로운 가상환경을 만들어 진행해보았다.
    
    ```bash
    conda create -n env03
    ```
    
- 새로운 가상환경은 python 버전이 3.9로 설치가 되었고 여기에 pandas-profiling을 설치해보았다.
    
    ```bash
    pip install pandas-profiling
    ```
    
- 이후 jupyter notebook으로 들어가 import를 하였더니 성공적으로 잘 되었다.
