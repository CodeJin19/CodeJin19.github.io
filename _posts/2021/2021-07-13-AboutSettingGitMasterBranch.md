---
title: '깃헙 마스터 브랜치 생성하기'
categories:
  - github
tags:
  - github
  - master
  - main
  - branch
date: 2021-07-13 17:35:13 +0900
last_modified_at: 2022-08-02 22:37:04 +0900
---

# main branch?

최근 하둡 공부를 시작하면서 오랜만에 새로운 레포지토리를 생성했는데, 기본 브랜치 이름이 master가 아니라 main으로 생성됐다.

main을 기본 브랜치로 사용해도 큰 차이는 없지만, `git push origin master`를 `git push origin main`으로 치려니 맛이 안 났다.

그래서 레포지토리를 생성할 때 master를 기본 브랜치로 생성하는 방법을 찾았다.

<br>

# master branch 생성하기

우선 tmp라는 레포지토리를 생성했다.

아래 캡처와 같이 main 브랜치를 기본으로 생성한 것을 확인할 수 있다.

<br>

![tmp_repository](/images/2021/2021-07-13-AboutSettingGitMasterBranch_2.TmpRepository.JPG)

<br>

새로운 레포지토리 생성 페이지를 자세히 보면 main 브랜치 관련 설정에 대한 안내문을 볼 수 있다.

<br>

![change_settings](/images/2021/2021-07-13-AboutSettingGitMasterBranch_3.ChangeSettings.JPG)

<br>

settings를 클릭해서 이동하면 아래와 같이 기본 브랜치 이름을 설정할 수 있는데, 이 부분을 master로 변경하고 update를 누르면 된다.

<br>

![change_settings](/images/2021/2021-07-13-AboutSettingGitMasterBranch_4.ChangeSettings.JPG)

<br>

레포지토리를 다시 생성해보면 master 브랜치가 기본으로 생성된 것을 확인할 수 있다.

<br>

![tmp_repository](/images/2021/2021-07-13-AboutSettingGitMasterBranch_6.TmpRepository.JPG)
