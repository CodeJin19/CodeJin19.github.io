---
title: "kramdown 이슈"
categories:
  - blog
tags:
  - blog
  - github_blog
  - jekyll
  - kramdown
date: 2022-02-28 16:07:26 +0900
last_modified_at: 2022-02-28 16:07:26 +0900
---

# 상황 정리

1. 블로그 포스트에서 이미지가 정상적으로 뜨지 않는 버그를 발견하고 해결했다.

2. 해당 이슈를 포스트로 기록하기 위해 2년만에 로컬에서 지킬 블로그를 실행했다.

3. 너무 오랜만에 블로그를 실행해서인지, 노트북을 포맷해서인지 환경 이슈로 인해 지킬 블로그를 실행 시 에러가 발생했다.

4. 깃헙 레포지토리의 블로그를 새로 받기 위해 [포스트](https://codejin19.github.io/blog/Making_Github_Blog_2/)를 참조하여 임시 블로그를 새로 생성하고 실행했다.

5. 임시 블로그도 실행할 수 없었다.

<br>

[지난 포스트](https://codejin19.github.io/blog/Making_Github_Blog_6/)에서 WEBrick 이슈를 해결함으로써 샘플 블로그를 만들고 실행할 수 있었다.

<br>

# 또 다른 이슈

하지만 로컬에서의 환경 이슈로 인한 블로그 실행 불가 에러는 여전히 남아있었다.

`bundle exec jekyll serve` 명령어로 실행하면 아래와 같은 에러가 발생했다.

```
Bundler could not find compatible versions for gem "github-pages":
  In snapshot (Gemfile.lock):
    github-pages (=207)

  In Gemfile:
    github-pages

Running `bundle update` will rebuild your snapshot from scratch, using only
the gems in your Gemfile, which may resolve the conflict.

Bundler could not find compatible versions for gem "kramdown":
  In Gemfile:
    kramdown (>= 2.3.1)

    github-pages was ersolved to 207, which depends on
      kramdown (=2.3.0)

Could not find gem 'kramdown (= 2.3.0)', which is required by gem 'github-pages', in locally installed gems.

The source contains the following gems matching 'kramdown':
  * kramdown-2.3.1
```

<br>

정확하지는 않지만, 눈치껏 kramdown gem의 버전 문제일 거라고 추측했다.

에러 메세지에 적힌 `bundle update`도 해봤고, kramdown gem을 2.3.0으로 재설치도 했지만, 어떤 방법을 해도 같은 에러가 발생했다.

<br>

# 해결책

구글링 끝에 [지킬 깃헙에 관련 이슈 페이지](https://github.com/jekyll/jekyll-help/issues/243)에서 해답을 찾을 수 있었다.

이슈를 생성한 사람이 말한대로,

1. gemfile.lock 삭제
2. bundle exec jekyll build

를 통해 해결했다.

<br>

# gemfile이란?

- gemfile
  - 본 프로젝트에서 사용하는 gem을 기록, 관리하는 파일
  - 따라서 프로젝트에 gem이 추가로 필요한 경우, gemfile에 해당 gem을 추가하는 방식으로 관리한다
- gemfile.lock
  - 실제로 설치된 gem 리스트

<br>

# 정리

kramdown gem의 버전 충돌로 인해 로컬에서 지킬 블로그 실행 불가 이슈가 발생했다.

1. gemfile.lock을 삭제하여 설치된 gem 파일들을 모두 삭제하고
2. `bundle exec jekyll build`로 gem 파일들을 다시 설치함으로써 해결했다.

결국 환경 관련 이슈 가장 강력한 해결책은 **재설치**다.