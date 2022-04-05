---
title: "NameError: name 'Tagger' is not defined"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-03-09 12:18:00
categories: [Error]
tags: [colab, mecab, tagger]
math: true
mermaid: true
---
## Error

- 구글 colab에서 mecab을 설치 후 다음과 같은 명령어를 실행했더니 에러가 발생하였다.
    
    ```python
    # mecab 설치
    !git clone https://github.com/SOMJANG/Mecab-ko-for-Google-Colab.git
    %cd Mecab-ko-for-Google-Colab
    !bash install_mecab-ko_on_colab190912.sh
    
    # mecab 실행
    from konlpy.tag import Mecab
    m = Mecab()
    ```
    
- 에러
    
    ```python
    NameError                                 Traceback (most recent call last)
    /usr/local/lib/python3.6/dist-packages/konlpy/tag/_mecab.py in __init__(self, dicpath)
        107         try:
    --> 108             self.tagger = Tagger('-d %s' % dicpath)
        109             self.tagset = utils.read_json('%s/data/tagset/mecab.json' % utils.installpath)
    
    NameError: name 'Tagger' is not defined
    
    During handling of the above exception, another exception occurred:
    
    Exception                                 Traceback (most recent call last)
    ```
    

## Error 해결

- mecab을 다음 링크를 통해 다운 받는다.
    
    ```python
    # konlpy, Mecab 형태소 분석기 설치 스크립트 실행
    !curl -s https://raw.githubusercontent.com/teddylee777/machine-learning/master/99-Misc/01-Colab/mecab-colab.sh | bash
    ```
    

## 참고 사이트

[구글 코랩(Google Colab)에서 Mecab 형태소 분석기, konlpy 쉽게 설치하기](https://teddylee777.github.io/colab/colab-mecab)
