---
layout: post
title:  "깃허브 블로그 만들기3"
date:   2019-07-11 00:21:33 +0900
categories: etc
author: "CodeJin19"
---
이번에는 로컬로 만든 블로그를 github에 올려서 온라인으로 띄워보자.

github에 사용자이름.github.io 라는 이름의 레포지토리를 만든다.

마음에 드는 테마를 찾았으면, 그 테마를 다운받는다.

명령 프롬프트를 켜서 블로그가 있는 폴더로 이동 후 다음의 명령어들을 입력한다.

{% highlight ruby %}
git init
git remote add origin (레포지토리 URL)
git add .
git commit -m "first commit"
git push origin master
{% endhighlight %}
