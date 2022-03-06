---
title: "non fast forward 에러에 관하여"
categories:
  - git
tags:
  - git
  - non_fast_forward
date: 2020-02-10 15:22:43 +0900
last_modified_at: 2020-02-10 15:22:43 +0900
---
방학을 맞아 다시 블로그를 시작해야지라고 마음을 먹었다. 기존에는 블로그 포스트를 깃헙에서 바로 만들었었는데, 올해에는 로컬에서 편집해서 깃헙에 올리고 싶다는 꿈이 생겼다. 열심히 편집을 하고, 커밋을 하니 에러가 발생했다. 에러메세지는 아무리 간단하더라고 읽기가 싫다. 이를 참고 읽어보니 non-fast-forward update가 주요 단어 같아보여 구글신에게 물어봤다. non-fast-forwad update는 로컬 저장소와 원격 저장소간의 데이터 최신화(?)문제라고 한다. (내 얕은 지식으로는 이렇게밖에 표현이 안 된다)

즉, 내 깃헙 레포지터리에 있는 데이터와 로컬기기에 있는 데이터가 서로 달라 충돌이 발생한 것이다. 조금 더 풀어쓰자면...

1. 내 깃헙 레포지터리에는 A 버전의 데이터가 있었고, 로컬기기에도 A 버전의 데이터가 있었다.

2. 깃헙 레포지터리에 업데이트가 있었고, 이제 깃헙 레포지터리는 A'버전의 데이터가 있다.

3. 로컬기기 역시 데이터에 수정이 있었고, 로컬기기에는 B버전의 데이터가 있다.

4. 두 저장소의 데이터가 포함관계가 아닌 상태가 되어 서로 다른 부분들에서 충돌이 발생한다.

라는 게 내가 이해한 non-fast-forward update 에러다.

나는 내 블로그를 장장 4개월동안 묵혔다가 이제 첫 커밋인데, 무슨 충돌이 일어난 것일까.. 아무리 생각해도 떠오르는 것이 없어 블로그 레포지토리를 삭제했다가 다시 만들었다. (덕분에 내 깃헙 커밋 기록들이 날라갔다. 나는 남아있는 줄 알았지...) 하지만 레포지토리를 다시 만들어도 같은 에러가 발생했다.

천천히 내 레포지토리를 둘러보니, 풀 리퀘스트가 있었고 (지킬, 혹은 지킬 테마의 dependency 문제로 인한 수정(?) 요청으로 추정한다) 이로 인해 내 로컬기기와 충돌이 났었던 것이다. 내가 제대로 한 건지는 모르겠지만, 대충 풀 리퀘스트를 수행하여 머지했고, 변경된 데이터를 로컬기기로 갖고온 후, 커밋을 하니 정상적으로 작동했다.