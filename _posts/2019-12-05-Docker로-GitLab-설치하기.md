---
date: 2019-12-05T10:16:00.000Z
layout: post
title: Docker로 GitLab 설치하기
subtitle: Docker와 GitLab을 사용하여 Private 한 Remote Git Repository 구축하기
description: >-
  망이 분리된 환경에서 내부 인원을 위한 Git Repository 운영할 필요가 생겼다.
  이런 상황에서 사용하기 좋은 GitLab을 Docker를 이용하여 설치 해보자.
image: >-
  /assets/img/uploads/2019-12-05/Docker로-GitLab-설치하기.png
optimized_image: >-
  /assets/img/uploads/2019-12-05/Docker로-GitLab-설치하기-small.png
category: tutorial
tags:
  - private
  - git
  - gitlab
  - docker
author: lonelywolf
paginate: true
---

Git은 **VCS(Version Control System)** 의 일종으로, 소프트워어의 작업 히스토리를 기록하고 그 버전을 관리 하기 위해서 사용되는 **분산 버전 관리 시스템**이다. 현대 소프트웨어 개발 업무에 **소스코드 관리 툴**은 빼놓을수 없는 요소이다.

Remote Git Repository을 Hosting 해주는 업체로는 대표적으로 [GitHub](https://github.com/), [Bitbucket](https://bitbucket.org/), [GitLab](https://gitlab.com/) 등이 있으며, 설치형 Repository 를 제공하는 업체로는 [Bitbucket](https://bitbucket.org/), [GitLab](https://gitlab.com/), 그리고 드물게 윈도우용 설치 패키지를 제공하는 [Gitblit](http://gitblit.com/) 등이 있다.

종종 업무를 위한 네트워크가 분리되어있는 회사에서 사내 Git Repository를 구축고 싶은 경우가 있는데, 이때는 설치형 Repository중 하나를 선택하여 사내망에 설치를 하면 된다. 나도 이러한 환경을 구성할 필요(및 책임)가 생겨서 설치형 시스템중 가장 유명한 **GitLab**을 선택 했다.

GitLab은 Git의 원격 저장소뿐만 아니라 코드 리뷰, 이슈 트래커 기능 및 CI/CD 기능까지 어느 수준까지는 제공을 한다. 설치형 Github라는 컨셉으로 시작된 프로젝트이기 때문에 Github와 비슷한 면이 많다.

사용할수 있는 버전은 CE(Community Edition)와 EE(Enterprise Edition)가 있으며 그 차이에 대해서는 [여기](https://about.gitlab.com/install/ce-or-ee/)서 확인할 수 있다. 간단히 말하자면, `CE`는 **MIT Expat license**로 제작된 **Open Source Project**이고, `EE`는 CE와 같은 core에 추가 기능을 구현하여 제공한다고 할 수 있다. 여기 저기 알아본 바로는 CE의 기능만으로 충분히 필요한 만큼 사용할 수 있다고 하므로, 나중에 업그레이드를 하더라도 우선 CE를 설치하는 방향으로 결론을 내렸다.

우선 GitLab을 설치하기 위한 [페이지](https://about.gitlab.com/install/?version=ce)로 들어간다. 다양한 설치방법이 있는데 나는 Docker를 이용한 설치를 하려고 하므로 **Other official installation methods** 항목에서 **Docker**를 찾아서 클릭한다. Docker는 요즘 많이 사용하는 Container System으로, Docker를 사용하면 내가 설치할 장비의 소프트웨어 환경에 영향을 받지 않고 항상 같은 사용 경험을 가지는 환경을 쉽게 설치/제거 할 수 있다. [Official GitLab Docker Image](https://docs.gitlab.com/ce/install/docker.html)에 대한 설명을 볼수 있으며, 내부 링크로 상세한 [설치 및 사용 가이드](https://docs.gitlab.com/omnibus/docker/)를 제공한다.

Docker를 이용한 설치 방식은 3가지를 제공한다.
* [Docker Image를 Docker Engine에 직접 실행](https://docs.gitlab.com/omnibus/docker/#run-the-image)
* [Docker를 다양한 Cluster에 배포](https://docs.gitlab.com/omnibus/docker/#install-gitlab-into-a-cluster)
* [docker-compose를 사용하여 Docker 배포](https://docs.gitlab.com/omnibus/docker/#install-gitlab-using-docker-compose)

나는 설정을 관리하고 쉽게 설치 및 제거를 하기 위해서 **docker-compose**를 이용 할 예정이다.

GitLab을 기본 설정으로 실행하기 위한 `docker-compose.yml` 파일의 내용을 아래와 같이 작성한다. 

```yml
web:
  image: 'gitlab/gitlab-ce:latest'
  restart: always
  hostname: 'gitlab.example.com'
  environment:
    GITLAB_OMNIBUS_CONFIG: |
      external_url 'https://gitlab.example.com'
      # Add any other gitlab.rb configuration here, each on its own line
  ports:
    - '80:80'
    - '443:443'
    - '22:22'
  volumes:
    - '/srv/gitlab/config:/etc/gitlab'
    - '/srv/gitlab/logs:/var/log/gitlab'
    - '/srv/gitlab/data:/var/opt/gitlab'
```

`GITLAB_OMNIBUS_CONFIG`는 GitLab에서 Docker Image를 만들때 미리 정의해둔 환경변수로, 해당 URL로 GitLab의 **외부 URL**을 설정할 수 있다. 사용하지 않을 경우 해당 설정은 생략 할 수 있다. `volumes`의 경우에 `Host의 경로:Container 내부의 경로`이므로, Host의 경로를 자신의 system 환경에 맞게 잘 작성을 해준다. 각각의 저장소 구성은 아래과 같다.

<table>
  <thead>
    <th>Local location</th>
    <th>Container location</th>
    <th>Usage</th>
  </thead>
  <tbody>
    <tr>
      <td>/srv/gitlab/data</td>
      <td>/var/opt/gitlab</td>
      <td>For storing application data</td>
    </tr>
    <tr>
      <td>/srv/gitlab/logs</td>
      <td>/var/log/gitlab</td>
      <td>For storing logs</td>
    </tr>
    <tr>
      <td>/srv/gitlab/config</td>
      <td>/etc/gitlab</td>
      <td>For storing the GitLab configuration files</td>
    </tr>
  </tbody>
</table>

`docker-compose.yml` 파일의 작성이 끝나고 저장을 하고 나서, 해당 파일이 있는 Directory로 이동한다. (작성 파일과 같은 Directory에 있는지 확인하고) `docker-compose up -d`를 실행하여 GitLab Docker을 시작할 수 있다.

`docker ps`를 사용하여 Container가 잘 실행 되었음을 확인 할 수 있다

![Docker run and check image](/assets/img/uploads/2019-12-05/Docker로-GitLab-설치하기-docker-run.png "Docker run and check image")

실행 한 Container에 대한 로그를 확인하고 싶은 경우 (예를 들어 실행 완료가  너무 오랫동안 일어나지 않는 경우) `docker logs {Container Name}`으로 해당 Container의 로그를 확인 할 수 있다.

![Docker log check image](/assets/img/uploads/2019-12-05/Docker로-GitLab-설치하기-docker-logs.png "Docker log check image")