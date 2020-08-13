---
title: "깃헙 블로그 만들기2"
categories:
  - blog
tags:
  - blog
  - github_blog
  - jekyll
date: 2019-07-08 23:02:38 +0900
last_modified_at: 2020-08-12 15:36:06 +0900
---
지난 포스트에서는 지킬을 활용해 블로그를 로컬에 만드는 방법을 살펴보았다.

이번에는 테마를 바꾸는 방법에 대해 알아보자.

현재 이 블로그 테마는 gravity이다.

다른 테마들은 http://jekyllthemes.org/ 여기서 확인할 수 있다.

마음에 드는 테마를 찾았으면, 그 테마를 다운받는다.

압축을 풀고, 그 안의 모든 파일들을 기존에 만든 my-awesome-site 폴더에 덮어씌운다.

그러면 index.html파일과 index.md파일 두 개가 있을텐데, index.md파일을 삭제한다.

{% highlight ruby %}
bundle exec jekyll serve
#=> http://localhost:4000에 접속
{% endhighlight %}

지난 명령어들을 다시 입력하면 테마 적용 완료!
