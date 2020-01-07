---
date: 2020-01-07T10:07:00+09:00
layout: post
title: GitLab Runner로 CI/CD 구성하기
subtitle: GitLab에서 CI(Continuous Integration), CD(Continuous Delivery) 환경 구성
description: >-
  지속적 통합과 지속적 배포는 현대 소프트웨어 개발에서 코드 품질 관리를 위해선 빼놓을 수 없는 프로세스이다.
  GitLab에서 Runner를 사용하여 지속적 통합/배포를 위한 환경을 구성하고 실제로 어떻게 적용하는지 알아보자.
image: >-
  https://about.gitlab.com/images/ci/ci-cd-test-deploy-illustration_2x.png
optimized_image: >-
  https://about.gitlab.com/images/ci/gitlab-ci-cd-logo_2x.png
category: technology
tags:
  - private
  - git
  - vcs
  - gitlab
  - docker
author: lonelywolf
paginate: true
comments: true
---

현대 사회에서 가장 보변적으로 언급되는 개발 방법론이 애자일(Agile) 개발 프로세스이다. 애자일 개발 방법론은 비효율적이고 일정 예측이 힘든 무계획적인 개발과, 변경에 느리고 계획 시간에 대한 비용이 많이 드는 계획이 너무 많은 개발(대다수의 고전적 개발 방법들) 사이의 타협점을 잡기 위해 나왔다. 애자일 개발 방법론의 핵심은 개발을 위한 전체 계획을 다 세우고 가는 방식이 아닌, 일정 주기를 가지고 끊임없이 제품 배포버전을 만들어내며 그때그때 요구사항을 추가하거나 수정해나가는 점진적인 방식으로 개발 프로세스를 가져간다는 점이다.

![Compare agile with waterfall][img-1]



### 태초에는..

### CVS


### SVN


### Git

<!-- LINKS -->
[blog-gitlab-install]: https://lonelywolflee.github.io/Docker%EB%A1%9C-GitLab-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0/
[about-gitlab-ci]: https://about.gitlab.com/product/continuous-integration/

<!-- IMAGES -->
[img-1]: /assets/img/uploads/2019-12-10/GitLab-Runner로-CI-CD-구성하기-1-compare.png "Compare agile with waterfall"
