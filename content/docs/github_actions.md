---
weight: 106
title: "Github_actions"
description: ""
icon: "article"
date: "2023-11-30T17:28:28-05:00"
lastmod: "2023-11-30T17:28:28-05:00"
draft: true
toc: true
---


[github's explanation](https://docs.github.com/en/actions/quickstart)
[wokwi github actions](https://docs.wokwi.com/wokwi-ci/getting-started)


### testing github actions:  
download [act](https://github.com/nektos/act)

test github action:  
`mkdir /temp/artifacts`  
`sudo ~/bin/act -s WOKWI_CLI_TOKEN=[<get token>] --artifact-server-path /tmp/artifacts`  
> Note: probs wont work cuz token is wrong or something

[random error when running act](https://github.com/nektos/act/issues/329#issuecomment-1187246629)

finding where it is in git:  
![github actions](../../pics/github_actions.png)


### auto deploy page for rhit_docs.github.io