---
date: 2020-01-17T00:00:00+09:00
layout: post
title: 망 분리 환경에서 Spring Boot + Kotlin 개발환경 구성
subtitle: 망 분리 환경에서 최소한의 정책만 오픈하고 개발환경을 구성하기
description: >-
  Spring + Kotlin을 개발하기 위해서는 수많은 library와 plugin 들이 사용 된다.
  업무 네트워크가 외부와 격리 된 환경에서 최소한의 정책만을 열어둔 채로 개발환경을 갖추어보자.
image: >-
  /assets/img/uploads/2020-01-09/Git-Project-관리-전략-0-head-main.png
optimized_image: >-
  /assets/img/uploads/2020-01-09/Git-Project-관리-전략-0-head-small.png
category: technology
tags:
  - spring
  - spring boot
  - git
  - gitlab
  - lfs
  - gradle
  - gradle repository
  - 망분리
author: lonelywolf
paginate: true
comments: true
---

1. nexus 3 설치
2. lfs 구성
3. 기타 정책 오픈

```sh
# spring initializer
https://start.spring.io/

# gradle download
https://services.gradle.org
https://downloads.gradle-dn.com # redirection

# gradle build 구성을 위한 plugin
https://plugins.gradle.org
https://plugins-artifacts.gradle.org

# Kotlin: Loading script dependencies 에 관련된 것으로 보임
https://repo.spring.io

# 그 밖의 경로들
https://repo.jfrog.org https://jcenter.bintray.com
https://d29vzk4ow07wi7.cloudfront.net

# ? jcenter를 쓰면 사용 안함
https://repo.maven.apache.org
```

1. nexus 3 설치
2. lfs 구성
3. 기타 정책 오픈

막혀있는 곳을 찾기 위한 수동 빌드 명령

```bash
$ ./gradlew build --console rich --debug
```

<!-- LINKS -->

[git-flow]: https://nvie.com/posts/a-successful-git-branching-model/

<!-- IMAGES -->

[img-1]: https://nvie.com/img/git-model@2x.png "Git Flow Model"
