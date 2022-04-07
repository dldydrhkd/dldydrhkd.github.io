---
title: "AttributeError: Can't get attribute 'BERTClassifier' on <module '__main__' from 'path'"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-04-06 20:45:00
categories: [Error]
tags: [flask, kobert, torch.load]
math: true
mermaid: true
---

## Error

- Flask에서 model을 불러오려고 하니 다음과 같이 error가 발생하였다.
    
    ```python
    sentimentModel = torch.load('./model.pt', map_location='cpu')
    ```
    
    <img width="933" alt="스크린샷_2022-04-07_오전_9 37 59" src="https://user-images.githubusercontent.com/48857296/162195602-d6dda59a-7b92-48e7-9590-bb7b08c38e53.png">
    

## Error 해결

- `torch.save(model, 'model.pt')`로 저장하여 model 전체를 불러오려고 하니 어떤 모델인지 정의 되어 있지 않아 에러가 나는거 같았다.
- torch.save(model.state_dict(), 'model.pt')로 저장한 후 모델을 정의하고 정의된 모델에 load를 하여 가중치와 편향을 부여하는 방법으로 해결하였다.
    
    ```python
    model = BERTClassifier(bertmodel,  dr_rate=0.5).to(device)
    
    model.load_state_dict(torch.load('model_state_dict.pt', map_location='cpu'))
    ```
    

## 참고 사이트

[[Pytorch] 모델 저장 방법, 그리고 전체 저장과 state_dict 저장의 차이](https://jdjin3000.tistory.com/17)
