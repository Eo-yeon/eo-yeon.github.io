---
layout: post
title:  "goatCounter를 이용해서 조회수 서비스 적용하는 방법"
date:   2024-11-18
categories: [opensource study]
author: eoyeon
- pin: true
---

# 시작하기전 . . . 👻
댓글 기능도 넣고 나니 이제 블로그다운 느낌이 점차 살아나는 것 같아 좋군요! 😎
그런데 아직은 내가 쓴 글을 몇 명이 읽었는지, 정말 내 글이 읽히고 있는지 알 방법이 없네요.
그래서 오늘은 바로 **조회수 서비스**를 적용하는 방법에 대해 포스팅해보려고 합니다.

그럼, **시작해볼까요?** 😊

[블로그 구축 포스팅 보러가기](https://eo-yeon.github.io/posts/first/)  
[댓글 서비스 적용 포스팅 보러가기](https://eo-yeon.github.io/posts/comment/)

---

## 1. goatcounter사이트 이용
- **1.0 [goatcounter 사이트](https://www.goatcounter.com/)에 접속합니다.**  

![홈페이지 화면 스크린샷](/assets/img/2024-11-11-goatcounter_1.PNG)

- **1.1 sign up 버튼을 클릭합니다.**  

- **1.2 필요한 정보들을 입력합니다.**
    - **Code**: goatcounter를 사용할 때의 개인 코드
    - **Site domain**: 내 블로그 주소 (ex: `name.github.io`)
    - **Email address**: 사용할 이메일 주소
    - **Password**: 사용할 비밀번호
    - **Fill in 9 here**: 9 입력  

![정보 입력](/assets/img/2024-11-11-goatcounter_2.PNG)

- **1.3 sign up 버튼 클릭**

> sign up을 완료하면 goatcounter 사이트가 생성됩니다!

- **1.4 우측 상단의 Settings 클릭**  
![Settings 버튼](/assets/img/2024-11-11-goatcounter_3.PNG)

- **1.5 settings -> Allow adding visitor counts on your website 항목 체크**  
![Allow adding visitor counts on your website](/assets/img/2024-11-11-goatcounter_4.PNG)

- **1.6 save 버튼 클릭**

## 2. Visual Studio Code 작업

### 2.1 _config.yml 파일 수정하기
- **2.1.1 블로그의 루트 디렉터리에 있는 _config.yml 파일 열기**
    아래 내용을 수정합니다:

```yaml
analytics:
  google:
    id: # fill in your Google Analytics ID
  goatcounter:
    id: name
  umami:
    id: # fill in your Umami ID
    domain: # fill in your Umami domain
  matomo:
    id: # fill in your Matomo ID
    domain: # fill in your Matomo domain
  cloudflare:
    id: # fill in your Cloudflare Web Analytics token
  fathom:
    id: # fill in your Fathom Site ID
```

- **name**에는 goatcounter 가입 시 입력했던 코드 값을 입력합니다.

- **2.1.2 provider 부분 수정하기**
아래 내용을 수정합니다.

```yaml
pageviews:
  provider: goatcounter
```

- **2.1.3 저장**  
![_config.yml 파일](/assets/img/2024-11-11-goatcounter_5.PNG)


### 2.2 변경사항 커밋 및 푸시하기
- 모든 파일 수정 후 GitHub에 커밋하고 푸시합니다 !

```shell
git add .
git commit -m "Add goatcounter"
git push
```

---

이제 자신의 goatcounter 사이트에서 대시보드를 확인하면 **조회수 통계**를 볼 수 있습니다. 또한 블로그 포스팅 오른쪽에도 조회수가 표시됩니다!  
![goatcounter 대시보드](/assets/img/2024-11-11-goatcounter_6.PNG)

![포스팅 조회수 확인](/assets/img/2024-11-11-goatcounter_7.PNG)

---

### 주의
현재는 GitHub Pages 주소를 직접 입력해야만 블로그에 접근할 수 있습니다. 따라서 블로그 주소를 알고 있지 않은 사람은 조회할 수 없다는 한계가 있습니다. 😭  

---

### 다음 포스팅
다음 포스팅에서는 Google 및 Naver 검색 엔진을 통해 블로그를 검색 가능하게 만드는 방법을 알려드리겠습니다! 그럼 안뇽 🖐🖐