---
title: "Attempting to deserialize object on a CUDA device but torch.cuda.is_available() is False. If you are running on a CPU-only machine, please use torch.load with map_location=torch.device('cpu') to map your storages to the CPU."
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-02-22 09:31:00
categories: [Error]
tags: [cpu, deep learning, gpu, kobert, machine learning, nlp]
math: true
mermaid: true
---

## Error

- GPU로 학습하여 저장한 모델 전체를 cpu로 불러오니 에러가 발생하였다.
    
    <img width="801" alt="스크린샷_2022-02-22_오전_9 35 28" src="https://user-images.githubusercontent.com/48857296/161662834-02718c1d-f9ff-4f3d-b8d7-8d495d4ac93e.png">
    

## Error 해결

- 코드를 다음과 같이 변경하여 불러오니 해결되었다.
    
    ```bash
    //변경 전
    model1 = torch.load('./7emotions_model.pt')
    
    //변경 후
    model1 = torch.load('./7emotions_model.pt',map_location='cpu')
    ```
    

# 참고 사이트

[모델 저장하기 & 불러오기 - PyTorch Tutorials 1.10.2+cu102 documentation](https://tutorials.pytorch.kr/beginner/saving_loading_models.html)
