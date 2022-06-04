---
title: "깃헙 블로그 다시 만들기 3"
categories:
  - blog
tags:
  - blog
  - github_blog
  - jekyll
  - jekyll_theme
date: 2020-08-31 16:41:10 +0900
last_modified_at: 2022-06-04 14:47:49 +0900
---

# 깃헙 블로그에 테마 적용하기

## 테마 다운로드

지난 포스트에서는 명령프롬프트와 지킬을 통해 블로그를 만들었다.

이번 포스트에서는 만든 블로그에 테마를 적용해보겠다.

지킬 블로그는 다양한 테마를 적용할 수 있는데, [이 페이지](http://jekyllthemes.org/)에서 테마들을 살펴볼 수 있다.

내가 처음 사용한 테마는 gravity라는 테마였고, 지금 사용하는 테마는 so simple이라는 테마다.

그래서 이번 포스트에서는 so simple 테마를 적용해보겠다.

<br>

우선 so simple 테마를 다운로드해야한다.

[so simple 레포지토리](https://github.com/mmistakes/so-simple-theme)에서 받을 수 있다.

<br>

![so-simple-theme_repo](/images/2020/2020-08-31-Making_Github_Blog_3_1.so-simple-theme_repo.jpg)

<br>

링크에 들어가서 위 이미지와 같이 `code` 버튼을 누르고 `Download ZIP`을 눌러 다운받아 압축을 풀자.

<br>

## README 따라서 테마 설치하기

어떤 프로그램을 설치하려면 설치 안내를 따라하듯, 테마를 적용하려면 레포지토리의 README.md에 있는 [Installation](https://github.com/mmistakes/so-simple-theme#Installation) 부분을 따라하면 된다.

우선, Gemfile에 다음을 추가한다.

```gemfile
gem "jekyll-theme-so-simple"
```

<br>

![gemfile](/images/2020/2020-08-31-Making_Github_Blog_3_2.gemfile.jpg)

<br>

다음으로 _config.yml에 아래 코드를 삽입하라고 적혀있는데,

```yml
theme: jekyll-theme-so-simple
```

가만히 살펴보니, newblog의 _config.yml에 위의 코드를 추가한 것보다 더 많은 코드들이 so-simple-theme-master의 _config.yml 파일에 있었다.

그래서 그냥 so-simple-theme-master의 _config.yml에 있는 전체 내용을 newblog 디렉토리의 _config.yml에 복붙했다.

<br>

![config.yml_after](/images/2020/2020-08-31-Making_Github_Blog_3_3.config.yml_after.jpg)

<br>

마지막으로 아래 명령어를 실행하라고 적혀있다.

```cmd
bundle install
```

지난 포스트에서와 같이 `win + r`, `cmd`로 명령 프롬프트를 연다.

명령프롬프트에서 `cd` 명령어를 통해 내 블로그가 있는 디렉토리로 이동한다.

위 명령어를 입력한다.

<br>

![cmd_bundle_install](/images/2020/2020-08-31-Making_Github_Blog_3_4.cmd_bundle_install.jpg)

<br>

설치가 완료됐으면, 지난번과 같이 `bundle exec jekyll serve` 명령어를 통해 블로그를 확인해 보자

<br>

![cmd_bundle_exec_jekyll_serve](/images/2020/2020-08-31-Making_Github_Blog_3_5.cmd_bundle_exec_jekyll_serve.jpg)

<br>

![local](/images/2020/2020-08-31-Making_Github_Blog_3_6.local.jpg)

<br>

혹시 테마가 적용되지 않았다면, Gemfile과 _config.yml을 수정한 후 저장하지 않았는지 확인하자.

일단 테마 설치는 성공한 것 같은데, 페이지 상단에 네비게이션 바가 안 보인다.

그럼 이제 네비게이션 바를 띄워보자.

<br>

## 네비게이션 바 띄우기

README를 더 읽어보니, [Structure](https://github.com/mmistakes/so-simple-theme#Structure)부분에서 so simple 테마를 위한 디렉토리 구조가 myblog 디렉토리 구조와 다르다는 것을 알 수 있었고,

so-simple-theme-master 디렉토리에서 `_data`, `_include`, `_layouts`, `_sass`, `assets` 디렉토리와 `_config.yml`, `.gitignore`, `index.md` 파일을 옮겨야 한다는 것을 알 수 있다.

하지만 우리는 위에서 `_config.yml`을 작업했기 때문에 `_config.yml`은 옮기지 않아도 된다.

그리고 `.gitignore`파일은 무시해도 되기 때문에, 5개의 디렉토리와 `index.md`파일만 myblog 디렉토리에 옮겨주면 된다.

디렉토리와 파일들을 모두 옮긴 뒤, myblog에 원래 있던 `index.markdown`파일은 삭제했다.

<br>

다음은 모든 작업을 마치고, 명령프롬프트에서 `bundle exec jekyll serve`를 실행한 결과다.

<br>

![local](/images/2020/2020-08-31-Making_Github_Blog_3_7.local.jpg)

<br>

이제 네비게이션 바도 잘 나온다.

이렇게 지킬 블로그에 so simple 테마를 무사히 적용했다!