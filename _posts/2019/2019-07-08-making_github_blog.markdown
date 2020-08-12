---
title: "깃허브 블로그 만들기1"
categories:
  - blog
tags:
  - blog
  - github_blog
  - jekyll
date: 2019-07-08 19:45:17 +0900
last_modified_at: 2020-08-12 15:35:50 +0900
---
깃허브에서 바로 블로그를 만들 수 있는지는 잘 모르겠지만, 지킬을 활용하면 더욱 쉽게 깃허브 블로그를 만들 수 있다.

따라서 이를 위해 깃, 루비, 지킬을 설치해야 한다.

무사히 설치를 마친 후, 윈도우 명령 프롬프트에서

{% highlight ruby %}
jekyll new my-awesome-site
cd my-awesome-site
bundle exec jekyll serve
#=> http://localhost:4000에 접속
{% endhighlight %}

이러면 지킬을 통해 간단히 블로그를 만들 수 있다!
