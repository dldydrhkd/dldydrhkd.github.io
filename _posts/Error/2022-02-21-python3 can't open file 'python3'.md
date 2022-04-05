---
title: "python3: can't open file 'python3': [Errno 2] No such file or directory"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-02-21 21:10:00
categories: [Error]
tags: [jupyter notebook, pyspark, python3]
math: true
mermaid: true
---

## Error

- pyspark를 jupyter notebook으로 사용을 하기 위해 환경변수 설정을 해주었고 다시 되돌리기 위해 환경변수를 제거 했지만 그대로 jupyter notebook으로 돌아감
- 결국 고치려다 다음과 같이 환경변수를 설정해줬지만 에러가 발생
    
    ```bash
    #export PYSPARK_DRIVER_PYTHON=jupyter
    #export PYSPARK_DRIVER_PYTHON_OPTS=notebook
    export PYSPARK_DRIVER_PYTHON=python3
    export PYSPARK_DRIVER_PYTHON_OPTS=python3
    ```
    
    <img width="576" alt="스크린샷_2022-02-22_오전_9 26 15" src="https://user-images.githubusercontent.com/48857296/161662469-23254b9b-0ca1-488b-9bbb-979181b8101d.png">
    

## Error 해결

- `.bashrc`에서 두 줄을 주석처리 하였지만 env 명령어로 환경변수를 확인했을 때 그대로 남아 있었다.
    
    ```bash
    #export PYSPARK_DRIVER_PYTHON=jupyter
    #export PYSPARK_DRIVER_PYTHON_OPTS=notebook
    ```
    
- 계정을 나갔다 들어오거나 재부팅을 하면 환경변수가 사라진 것을 볼 수 있다.
- 위에서 난 에러는 쓸데 없이 python3를 붙여줘서 난 에러이다.
