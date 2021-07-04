---
date: 2020-01-17T00:00:00+09:00
layout: post
title: (연구노트 01) API Gateway with auth - 00. 계획 수립
subtitle: Apache APISIX를 사용한 API Gateway 인증 시나리오를 사용하기 위한 계획 수립 단계
description: >-
  오픈소스인 Apache APISIX 를 사용한 API Gateway에서 인증을 어떻게 구현하는지 연구해보자.
image: >-
  https://camo.githubusercontent.com/e31595f11b4de884b12a495de8539acaeaadfc03af70cd390742e11e52c12706/68747470733a2f2f73766e2e6170616368652e6f72672f7265706f732f6173662f636f6d6465762f70726f6a6563742d6c6f676f732f6f726967696e616c732f6170697369782e737667
optimized_image: >-
  https://camo.githubusercontent.com/e31595f11b4de884b12a495de8539acaeaadfc03af70cd390742e11e52c12706/68747470733a2f2f73766e2e6170616368652e6f72672f7265706f732f6173662f636f6d6465762f70726f6a6563742d6c6f676f732f6f726967696e616c732f6170697369782e737667
category: technology
tags:
  - apache
  - api
  - api gateway
  - opensource
  - apisix
  - auth
  - cloud
  - msa
author: lonelywolf
paginate: true
comments: true
---

  나는 사실 `MSA`이니 `DDD`이니 하는 것들을 맹목적으로 따르는 것들은 그다지 좋아하지 않는다. 심지어 CLOUD 이기 때문에, 프로젝트가 크기 때문에 같은 말들은 (경험상) 더욱 동의하지 않는 편이다.