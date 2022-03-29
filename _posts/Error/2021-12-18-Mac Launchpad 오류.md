---
title: Mac Launchpad 오류
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2021-12-18 12:40:00
categories: [Error]
tags: [Mac, launchpad]
math: true
mermaid: true
---

<aside>
💡 맥의 런치 패드에 삭제된 아이콘이 있고 새로 다운로드한 아이콘이 없는 상황

</aside>

## 해결 방법

- 터미널에 다음과 같이 명령어를 작성한다.
    
    ```bash
    defaults write com.apple.dock ResetLaunchPad -bool true; killall Dock
    ```
