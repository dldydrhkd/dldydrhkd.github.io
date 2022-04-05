---
title: "The kernel appears to have died. It will restart automatically by using XGBoost"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-03-25 10:10:00
categories: [Error]
tags: [XGBoost, jupyter notebook]
math: true
mermaid: true
---

## Error

- Jupyter notebook에서 XGBoost를 사용하기 위해 `python -m pip install xgboost`를 하였고 사용하려고 하니 다음과 같은 에러가 났다.
    
    ```jsx
    The kernel appears to have died. It will restart automatically by using 
    ```
    

## Error 해결

- OS 차이로 인한 에러인것 같다.
- `conda install -c anaconda py-xgboost` 로 설치하니 잘 돌아갔다.
