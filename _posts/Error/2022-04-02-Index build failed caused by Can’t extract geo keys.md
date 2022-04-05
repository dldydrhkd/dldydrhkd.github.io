---
title: "Index build failed :: caused by :: Can’t extract geo keys"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-04-02 17:12:00
categories: [Error]
tags: [2dsphere, createIndex, spring data mongodb]
math: true
mermaid: true
---

## Error

- mongoDB의 GeoJSON을 사용하기 위해 다음과 같이 mongoDB에 쿼리를 날렸더니 에러가 떴다.
    
    ```sql
    db.visitJeju.createIndex({location:"2dsphere"})
    ```
    
- Error
    
    <img width="676" alt="스크린샷_2022-04-02_오전_2 33 27" src="https://user-images.githubusercontent.com/48857296/161668935-ba9f1ba6-dc43-4fd3-adcd-8aada0761b92.png">
    

## Error 해결

- 무엇때문인지 ObjectId(’624708b37881cf12acabc8cc’) 요놈의 index를 못 만드는거 같아 조회를 해봤더니 다음과 같았다.
    
    <img width="1037" alt="스크린샷_2022-04-02_오후_5 17 35" src="https://user-images.githubusercontent.com/48857296/161668952-be62ea39-3087-438d-8246-62e328756519.png">
    
    > coordinates를 살펴보니 숫자가 들어가 있지 않고 string으로 들어가 있어 에러가 난 것이다.
    > 
- 바로 숫자로 고쳐 다시 돌려보니 Error가 해결 되었다.
