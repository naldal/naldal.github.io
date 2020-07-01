---
title: "[Spring Boot] 음악학원 홈페이지 제작 프로젝트 1일차"

toc: true
toc_sticky: true

categories:
  - springboot
  
tags:
  - AWS
  - 스프링부트
  - 웹
---

<br><br>

##사용기술

Backend : Spring Boot 2.1.7<br>
Frontend : Bootstrap<br>
Server Side Template : Mustache<br>
IDE : Intellij community<br>
Database : AWS RDS (Maria DB)<br>
Deploy : AWS EC2, Travis CI<br>
SCM : Git, Github, SourceTree<br>

  스프링 레거시를 이용한 맛집 예약 웹서비스 프로젝트를 마친지 3개월이 지났다. 그 동안 자료구조와 알고리즘 관련 공부에 집중했고 완벽하게는 아니지만 스스로 만족할만한 성장을 이뤄낸 것 같다. 지금 시작하는 음악학원 웹 서비스 제작 프로젝트는 필자의 어머니로부터 받은 일종의 외주다. (하지만 페이는 없다..) 하지만 스프링 부트를 이용한 무중단 배포서비스에 관심이 많았고, 예제가 아니라 실제적인 나만의 서비스로 구현하고자 하는 욕심이 컸기에 본 프로젝트를 시작했다.

  IDE는 전의 스프링 부트 프로젝트에서처럼 인텔리제이 커뮤니티 버전을 이용할 것이고 템플릿 또한 Mustache를 적극 사용할 예정이다. 이번 프로젝트를 통해서 포트폴리오+1은 물론 Spring Data JPA 및 Travis와 AWS 사용에 더욱 익숙해지길 바래본다.

## 프로젝트 빌드

```jsx
buildscript {
    ext {
        springBootVersion = '2.1.7.RELEASE'
    }
    repositories {
        mavenCentral()
        jcenter()
    }
    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
    }
}

apply plugin: 'java'
apply plugin: 'eclipse'
apply plugin: 'org.springframework.boot'
apply plugin: 'io.spring.dependency-management'

group 'com.soriel.music'
version '1.0-SNAPSHOT'
sourceCompatibility = 1.8

repositories {
    mavenCentral()
}

dependencies {
    testCompile group: 'junit', name: 'junit', version: '4.12'
    compile('org.springframework.boot:spring-boot-starter-web');
    testCompile('org.assertj:assertj-core:3.11.1')
    compileOnly('org.projectlombok:lombok')
    annotationProcessor('org.projectlombok:lombok')
}
```
<br>
프로젝트는 Maven이 아닌 Gradle로 세팅할 것이다. (솔직히 pom.xml의 너저분한 방식에 질려있었다) 디펜던시는 `spring-boot-starter-web`으로 기본적으로 Tomcat에 올릴 Spring MVC를 이용한 RESTful 서비스 관련 api들을 받아준다. 그리고 `org.assertj:assertj-core:3.11.1`로 강력한 테스트 툴인 [assertj](https://joel-costigliola.github.io/assertj/)를 이용한다. 추가적으로 롬복관련 디펜던시를 받아와주면 초기 빌드작업이 끝난다.

이제 이 프로젝트를 Github과 연동한다. 특히 주의해야 할 점은 `.idea`확장자가 Github에 올라가지 않도록 필히 gitignore에 추가해줘야 한다. `.idea`는 인텔리제이에서 프로젝트를 Import 할 때 쓰이기 때문에 혹여 다른 IDE를 사용중인 개발자가 이를 받아서 실행하는 것을 미연에 방지하는 것이다.

깃헙에 잘 push 됐으면 오늘은 여기서 끝!

↓ 여기에 계속해서 작업결과가 올라갈 것이다

[https://github.com/naldal/soriel-music-academy](https://github.com/naldal/soriel-music-academy)
<br>
<br>
