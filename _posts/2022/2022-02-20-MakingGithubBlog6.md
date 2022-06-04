---
title: "로컬 환경에서 지킬 블로그 실행 불가능 이슈"
categories:
  - blog
tags:
  - blog
  - github_blog
  - jekyll
  - webrick
date: 2022-02-20 17:30:26 +0900
last_modified_at: 2022-06-04 15:08:32 +0900
---

# 새로운 이슈

지난 주에 블로그 포스트에서 이미지가 뜨지 않는 에러를 발견하고 해결했었다.

오늘 해당 이슈를 포스팅하기 위해 로컬에서 지킬 블로그를 실행했더니 환경 이슈로 인하여 실행되지 않았었다.

환경 설정을 다시 하기 위해 재작년에 썼던 [깃헙 블로그 다시 만들기 2](https://codejin19.github.io/blog/Making_Github_Blog_2/)를 참고해서 샘플 블로그를 생성하고 실행했는데 이것조차 안 됐다.

<br>

## 2줄 요약

1. 오랜만에 로컬에서 지킬 블로그를 실행하려 했으나 안 됨
2. 지난 [포스트](https://codejin19.github.io/blog/Making_Github_Blog_2/)를 참고하여 로컬 환경에서 새로운 블로그 생성 후 실행했으나 안 됨

<br>

이번 포스트에서는 **지킬 블로그가 실행되지 않는 이유**와 **해결방법**을 정리한다.

<br>

# 새로운 에러

기존 포스트에서는 아래 4개의 명령어를 실행하면 블로그를 만들 수 있다고 했다.

1. gem install jekyll bundler
2. jekyll new myblog
3. cd myblog
4. bundle exec jekyll serve

하지만 4번 명령어를 실행해보면 아래와 같은 에러가 발생한다.

<br>

![WEBrick_error](/images/2022/2022-02-20-Making_Github_Blog_6.WEBrick_error.PNG)

<br>

```
                    ------------------------------------------------
Jekyll 4.2.1   Please append `--trace` to the `serve` command
                     for any additional information or backtrace.
                    ------------------------------------------------
```

<br>

처음에는 빨간색 글자가 가장 중요한 에러를 나타낼 것이라고 생각했다.

따라서 로그를 보고 4번 명령에 `--trace` 옵션을 추가해서 실행했었다.

<br>

![With_tace_option](/images/2022/2022-02-20-Making_Github_Blog_6.with_tace_option.PNG)

<br>

```
...  in `require`: cannot load such file -- webrick (LoadError)
```

<br>

하지만 webrick load error는 여전히 남아있엇고 구글에 webrick 이슈를 검색했다.

<br>

# WEBrick

WEBrick은 간단한 HTTP 웹 서버를 제공하는 Ruby 라이브러리인데 ([참조](https://en.wikipedia.org/wiki/WEBrick)), ruby 3.0부터 기본으로 설치되는 gem에서 빠졌기 때문에, 수동으로 추가 설치가 필요했다.

<br>

`bundle add webrick` 명령어로 WEBrick을 추가 설치해주자.

<br>

![Install_WEBrick](/images/2022/2022-02-20-Making_Github_Blog_6.install_WEBrick.PNG)

<br>

다시 실행해보면 잘 실행된다.

<br>

![works_well](/images/2022/2022-02-20-Making_Github_Blog_6.works_well.PNG)

<br>

# 정리

랩탑을 포맷하고 ruby를 재설치하면서 3.0 이상의 ruby를 설치했고,

3.0 이상부터는 WEBrick이 기본으로 설치되지 않기 때문에, 로컬 환경에서 WEBrick이 누락되었다.

이로 인해 ruby가 실행되지 않는 이슈가 발생했다.

따라서 누락된 WEBrick을 수동으로 설치함으로써 해당 이슈를 해결할 수 있었다.