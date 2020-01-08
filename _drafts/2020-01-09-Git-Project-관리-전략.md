---
date: 2020-01-08T00:00:00+09:00
layout: post
title: Git Project 관리 전략
subtitle: Git flow, GitHub flow, GitLab flow 에 대한 정리
description: >-
  우리는 개발 Project를 진행 하기 위해서 Branch 전략과 Release 관리에 대해 잘 생각 해보아야 한다.
  이 Post 에서는 가장 유명한 전략인 Git flow, GitHub flow, GitLab flow 를 통해 이를 살펴본다.
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

`Git`으로 효율적으로 협업하고 프로젝트의 관리를 잘 하기 위해서는 적절한 `Branching Strategy`와 `Release Management`가 동반 되어야 한다. 이러한 목적을 달성 하기 위해서 다양한 `Branch Model`이 제안 되었는데, 그 중에 가장 유명한 3개의 Model을 살펴보도록 한다. 작성은 아래의 링크를 참조하였다.

* [Git Flow][git-flow]
* [GitHub Flow][github-flow]
* [GitLab Flow][gitlab-flow]


## Git Flow
### 설명

![Git Flow Model][img-1]



## GitHub Flow
### 설명

![GitHub Flow Model][img-2]

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
