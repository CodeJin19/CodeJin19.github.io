---
title: 'Spring Boot 에러'
categories:
  - spring
tags:
  - spring
  - error
  - setup
date: 2023-08-03 23:36:10 +0900
last_modified_at: 2023-08-03 23:36:10 +0900
---

# Spring 공부 다시 시작

미루고 미루던 스프링 공부를 다시 시작하려고 굳은 마음을 먹고 영상을 틀었다.

영상을 따라 [spring initializr](https://start.spring.io/)에 들어가 스프링 프로젝트를 생성하고, inteliJ로 열어 빌드를 수행하니...

<br>

# A problem occurred configuring root project

에러가 발생했다.

에러 메세지는 아래와 같다.

```
A problem occurred configuring root project 'hello_spring'.
> Could not resolve all files for configuration ':classpath'.
   > Could not resolve org.springframework.boot:spring-boot-gradle-plugin:3.1.2.
     Required by:
         project : > org.springframework.boot:org.springframework.boot.gradle.plugin:3.1.2
      > No matching variant of org.springframework.boot:spring-boot-gradle-plugin:3.1.2 was found. The consumer was configured to find a library for use during runtime, compatible with Java 11, packaged as a jar, and its dependencies declared externally, as well as attribute 'org.gradle.plugin.api-version' with value '8.2.1' but:
          - Variant 'apiElements' capability org.springframework.boot:spring-boot-gradle-plugin:3.1.2 declares a library, packaged as a jar, and its dependencies declared externally:
              - Incompatible because this component declares a component for use during compile-time, compatible with Java 17 and the consumer needed a component for use during runtime, compatible with Java 11
              - Other compatible attribute:
                  - Doesn't say anything about org.gradle.plugin.api-version (required '8.2.1')
          - Variant 'javadocElements' capability org.springframework.boot:spring-boot-gradle-plugin:3.1.2 declares a component for use during runtime, and its dependencies declared externally:
              - Incompatible because this component declares documentation and the consumer needed a library
              - Other compatible attributes:
                  - Doesn't say anything about its target Java version (required compatibility with Java 11)
                  - Doesn't say anything about its elements (required them packaged as a jar)
                  - Doesn't say anything about org.gradle.plugin.api-version (required '8.2.1')
          - Variant 'mavenOptionalApiElements' capability org.springframework.boot:spring-boot-gradle-plugin-maven-optional:3.1.2 declares a library, packaged as a jar, and its dependencies declared externally:
              - Incompatible because this component declares a component for use during compile-time, compatible with Java 17 and the consumer needed a component for use during runtime, compatible with Java 11
              - Other compatible attribute:
                  - Doesn't say anything about org.gradle.plugin.api-version (required '8.2.1')
          - Variant 'mavenOptionalRuntimeElements' capability org.springframework.boot:spring-boot-gradle-plugin-maven-optional:3.1.2 declares a library for use during runtime, packaged as a jar, and its dependencies declared externally:
              - Incompatible because this component declares a component, compatible with Java 17 and the consumer needed a component, compatible with Java 11
              - Other compatible attribute:
                  - Doesn't say anything about org.gradle.plugin.api-version (required '8.2.1')
          - Variant 'runtimeElements' capability org.springframework.boot:spring-boot-gradle-plugin:3.1.2 declares a library for use during runtime, packaged as a jar, and its dependencies declared externally:
              - Incompatible because this component declares a component, compatible with Java 17 and the consumer needed a component, compatible with Java 11
              - Other compatible attribute:
                  - Doesn't say anything about org.gradle.plugin.api-version (required '8.2.1')
          - Variant 'sourcesElements' capability org.springframework.boot:spring-boot-gradle-plugin:3.1.2 declares a component for use during runtime, and its dependencies declared externally:
              - Incompatible because this component declares documentation and the consumer needed a library
              - Other compatible attributes:
                  - Doesn't say anything about its target Java version (required compatibility with Java 11)
                  - Doesn't say anything about its elements (required them packaged as a jar)
                  - Doesn't say anything about org.gradle.plugin.api-version (required '8.2.1')

* Try:
> Run with --info or --debug option to get more log output.
> Run with --scan to get full insights.
> Get more help at https://help.gradle.org.
```

<br>

# 원인

구글링을 해보니, 스프링부트 3.0부터는 JAVA 17부터 지원되는데, 로컬 환경 JAVA는 11이었다.

실제로 프로젝트 폴더 내의 build.gradle 파일을 확인해보면 JAVA 버전이 17임을 확인할 수 있다.

<br>

![InteliJ](/images/2023/2023-08-03-SpringBootError_1.InteliJ.JPG)

<br>

하지만 cmd 창을 통해 확인한 JAVA 버전은 11이다.

<br>

![CmdCheckJavaVersion](/images/2023/2023-08-03-SpringBootError_2.CmdCheckJavaVersion.JPG)

# 해결책

결국 JAVA 버전을 바꾼지 3달 만에 다시 재설치를 해야한다... ㅠㅠ
