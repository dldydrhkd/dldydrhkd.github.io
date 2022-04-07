---
title: "transformers Installation Error - Failed building wheel for tokenizers"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-04-05 22:32:00
categories: [Error]
tags: [kobert, transformers]
math: true
mermaid: true
---

## Error

- Kobert를 다운 받는 중 다음과 같은 에러가 발생했다.
    
    ```
    ERROR: Failed building wheel for tokenizers
    Failed to build tokenizers
    ERROR: Could not build wheels for tokenizers which use PEP 517 and cannot be installed directly
    ```
    

## Error 해결

- [link](https://www.rust-lang.org/tools/install)로 들어가 명령어를 copy 한 후 terminal에 입력해줬다.
    
    ```bash
    - `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`
    ```
    
- 터미널을 재시작 하고 `pip install transformers==2.5.1` 후 Kobert를 재설치 했더니 error가 해결 되었다.

## 참고 사이트

[[Solved] transformers Installation Error - Failed building wheel for tokenizers](https://lifesaver.codes/answer/installation-error-failed-building-wheel-for-tokenizers-2831)
