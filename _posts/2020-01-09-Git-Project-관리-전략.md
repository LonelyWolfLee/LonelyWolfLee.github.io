---
date: 2020-01-08T00:00:00+09:00
layout: post
title: Git Project 관리 전략
subtitle: Git Flow, GitHub Flow, GitLab Flow 에 대한 정리
description: >-
  우리는 개발 Project를 진행 하기 위해서 Branch 전략과 Release 관리에 대해 잘 생각 해보아야 한다.
  이 Post 에서는 가장 유명한 전략인 Git-Flow, GitHub Flow, GitLab Flow 를 통해 이를 살펴본다.
image: >-
  /assets/img/uploads/2020-01-09/Git-Project-관리-전략-0-head-main.png
optimized_image: >-
  /assets/img/uploads/2020-01-09/Git-Project-관리-전략-0-head-small.png
category: technology
tags:
  - git
  - git-flow
  - github
  - gitlab
  - workflow
author: lonelywolf
paginate: true
comments: true
---

`Git`으로 효율적으로 협업하고 프로젝트의 관리를 잘 하기 위해서는 적절한 `Branching Strategy`와 `Release Management`가 동반 되어야 한다. 이러한 목적을 달성 하기 위해서 다양한 `Branch Model`이 제안 되었는데, 그 중에 가장 유명한 3개의 Model을 가볍게 살펴보도록 한다. 작성은 아래의 링크를 참조하였다.

* [Git Flow][git-flow]
* [GitHub Flow][github-flow]
* [GitLab Flow][gitlab-flow]


## Git-Flow
### 소개

![Git Flow Model][img-1]

**Git-Flow** 에서는 `feature`, `develop`, `release`, `hotfix`, `master` 이렇게 5 종류의 **branch**를 사용 할 것을 제안한다. 이중에 **develop**과 **master**가 `main branch`이며 나머지 3 가지 branch가 `support branch`이다. support branch는 remote에 push 될 필요가 없고, merge후 삭제 해도 무방하다. (상세 내용은 상단 링크 참조)

#### master

`Stable Version`의 code를 저장하고 실제로 배포를 하기 위한 branch이다. 언제나 제품으로 출시가 가능한 상태의 코드만 두고 적절히 `tag`를 붙인다.

#### develop

`master branch로 부터` 분리되며, 개발 feature 들이 추가되는 branch이다.

#### feature

`develop branch로 부터` 분리되며, 단일 feature를 개발 하기 위해 분리된 branch이다. 개발이 완료되면 `develop branch로 merge`된다.

#### release

필요한 feature들이 develop branch에 다 merge 되고 나면 배포를 해야 하는데, 이를 위한 product 준비 branch이다. `develop branch로 부터` 분리되며, 이후에는 test 등을 진행하며 bug fix commit만 추가한다. (일종의 staging 단계이다) 배포 할 준비가 되고 나면 `master branch와 develop branch로 merge`된다.

#### hotfix

이미 배포된 pruduct에 문제가 있을 경우 이를 해결하기 위한 branch이다. `master branch로 부터` 분리되며, 이후에는 해당 문제 해결을 위한 bug fix commit만 추가한다. 문제 해결 이후에 `master branch와 develop branch로 merge`된다.


### 개인적인 생각

**Git Flow** 전략은 배포 산출물 관리에 유리한 model 이다. 배포에 들어가는 노력이 크거나, 재 배포 시기가 길거나, 배포에 대한 위험 부담이 클때 쓰면 좋다. 그래서 명확한 산출물이 파일이나 서비스 형태로 추출되는 `Back-end`, `App` 형태의 Project에 적합하다.


## GitHub Flow
### 설명

![GitHub Flow Model][img-2]

**GitHub**은 **Git-Flow**가 너무 복잡하고, branch의 역할이 모호하다고 생각한다. 그래서 매우 간단한 **branch model**을 제안한다. GitHub Flow에서는 branch의 종류가 `master`, `feature` 이렇게 단 두 가지이다(GutHub은 feature라고 얘기하지 않지만 목적상 feature이므로 그렇게 지칭 하겠다). master branch를 `main branch`로 해서 `feature branch`가 생기며, 문제 해결 과정은 아래와 같다. (상세 내용은 상단 링크 참조)

1. master branch에서 feature나 idea에 맞게 branch를 분리한다. 
2. 개발을 진행하면서 적절한 단위로 commit을 한다.
3. 개발이 완료되면 


## GitLab Flow
### 설명

#### Production branch with GitLab flow

![Production branch with GitLab flow][img-3]

#### Environment branches with GitLab flow

![Environment branches with GitLab flow][img-4]

#### Release branches with GitLab flow

![Release branches with GitLab flow][img-5]


<!-- LINKS -->
[git-flow]: https://nvie.com/posts/a-successful-git-branching-model/
[github-flow]: https://guides.github.com/introduction/flow/
[gitlab-flow]: https://about.gitlab.com/blog/2014/09/29/gitlab-flow/

<!-- IMAGES -->
[img-1]: https://nvie.com/img/git-model@2x.png "Git Flow Model"
[img-2]: https://user-images.githubusercontent.com/6351798/48032310-63842400-e114-11e8-8db0-06dc0504dcb5.png "GitHub Flow Model"
[img-3]: https://about.gitlab.com/images/git_flow/production_branch.png "Production branch with GitLab flow"
[img-4]: https://about.gitlab.com/images/git_flow/environment_branches.png "Environment branches with GitLab flow"
[img-5]: https://about.gitlab.com/images/git_flow/release_branches.png "Release branches with GitLab flow"
