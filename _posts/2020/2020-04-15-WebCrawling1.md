---
title: "파이썬으로 웹 크롤링하기1"
categories:
  - crawling
tags:
  - crawling
  - python
  - beautiful_soup
date: 2020-04-15 16:54:28 +0900
last_modified_at: 2020-04-15 16:54:28 +0900
---

# Python 설치

[파이썬 공식 홈페이지 링크](http://www.python.org/downloads)

위의 파이썬 공식 홈페이지 링크에 가서 설치 프로그램을 다운받자. 메인화면에 최신 버전으로 다운받을 수 있는 버튼이 있다. 설치파일을 시작하면 하단부에 "Add Python (버전) to PATH" 옵션이 있는데 이 옵션을 선택하고 설치하면 된다.

<br>

# Module 설치

파이썬으로 크롤링을 하려면 requests 모듈을 써야하는데, 이 모듈을 추가로 설치해야 한다. cmd창에서 다음 명령어로 설치할 수 있다.

``` cmd
pip install requests
```

Beautiful Soup 라이브러리도 필요한데, 이 역시 추가로 설치가 필요하다. 마찬가지로 cmd창에서 다음 명령어로 설치할 수 있다.

```cmd
pip install beautifulsoup4
```

<br>

# 크롤링 기초

우선 Beautiful Soup를 사용하지 않고, requests 모듈만 사용해서 크롤링을 해보자.

```python
import requests

webpage = requests.get("https://www.naver.com/")
print(webpage.text)
```

위의 예제는 네이버 메인화면의 HTML 문서를 크롤링해서 출력한다. HTML문서에서 내가 원하는 데이터만 크롤링하기 위해서는 라이브러리의 도움이 필요한데, 이 역할을 하는 게 Beautiful Soup이다.

<br>

# Beautiful Soup 사용하기

```python
import requests
from bs4 import BeautifulSoup

webpage = requests.get("https://www.naver.com/")
soup = BeautifulSoup(webpage.content, "html.parser")

print(soup)
```
