---
title: You do not have permission to open the application
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2021-12-23 21:12:00
categories: [Error]
tags: [Big sur, DBeaver]
math: true
mermaid: true
---
<aside>
💡 어제까지 사용했던 DBeaver가 다음 날 다시 켰더니 열 수 있는 권한이 없다고 한다.

</aside>

## Error

![](https://images.velog.io/images/dldydrhkd/post/93d87f6b-9c6b-4bab-914b-83a8eab55147/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-12-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_9.10.44.png)

## 해결 방법

- `pkutil --check-signature /Application/앱이름.app` 을 터미널에서 실행해보자
    
    ![](https://images.velog.io/images/dldydrhkd/post/cccb7a2a-8cbf-44ea-9275-e133ed56a69c/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-12-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_9.06.54.png)
    
    > invalid 상태라고 뜬다.
    > 
- `codesign --force --deep --sign - /Applications/앱이름.app` 을 터미널에 실행 시켜 해결한다.
    
    ![](https://images.velog.io/images/dldydrhkd/post/00dc19a5-f751-4cef-912a-75662926dd44/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-12-23_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_9.07.56.png)
    
    > 완료 되면 앱을 실행 시킬 수 있게 된다
    > 

## 원인

- 모든 앱은 오용되거나 변조되지 않았는지 확인하기 위해 Apple의 서명을 받는다.
- 수정 과정에서 뭔가 서명이 잘못된거 같다고 생각된다.

## 참고 사이트

[[macOS] Big sur에서 권한이 없다며 어플리케이션이 안열리는 경우의 해결](https://doda.tistory.com/entry/macOS-Big-sur%EC%97%90%EC%84%9C-%EA%B6%8C%ED%95%9C%EC%9D%B4-%EC%97%86%EB%8B%A4%EB%A9%B0-%EC%96%B4%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98%EC%9D%B4-%EC%95%88%EC%97%B4%EB%A6%AC%EB%8A%94-%EA%B2%BD%EC%9A%B0%EC%9D%98-%ED%95%B4%EA%B2%B0)
