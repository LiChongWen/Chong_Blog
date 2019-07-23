---
title: "Gitflow及协同开发规范"
excerpt: "Gitflow及协同开发规范."
date: 2019-07-23
tags: ['Vue', 'Technology']
cover_image: './images/bg-2.jpg'
---


## Gitflow及协同开发规范


常用分支
# develop
- 开发分支，分支代码部署到开发环境。
- 开发同学们完成各自模块后提交合并到该分支进行自测、联调。
- 禁止直接在该分支上提交修改。
# alpha
- 测试分支，分支代码部署到测试环境。
- 完成版本开发并通过自测、联调后将较稳定的develop分支代码并入该分支交付测试团队转测。
# beta
- 演示分支，分支代码部署到demo环境。
- 经过多轮测试、debug后，将稳定的alpha分支代码并入该分支，预上线。
- 禁止直接在该分支上提交修改。
# master
- 整个项目最稳定的代码分支，分支代码部署到生产环境。
- 禁止直接在该分支上提交修改。
- 除版本发布或者发hotfix外，一般不合并代码到该分支。
- 除管理员外不要动该分支，不要动！不要动！不要动！
# hotfix
- 线上bug修复分支，用于紧急修复线上bug。
- 从master分支checkout出来，merge到beta分支或者alpha分支部署验证，验证通过过再合并到master和develop分支。
- 个人迭代分支
- 命名规则为：{version}/{yourName}，如v1.6/licl。
- 用于开发者每个版本的迭代，从develop分支checkout出来，完成开发后merge会develop分支。
- 每个开发者每个版本只维护一个该分支。
# bug修复分支
- 较复杂或需要花较多时间修复的bug需另其一个分支修改，以防阻塞其他工作进度。
- 命名规则： fix/{description}，如fix/loginError。
# 工作流程
1. 新版本开发

```c
 # 每天第一件事pull develop分支代码，保证本地代码最新
 git checkout develop
 git pull

 # checkout出各自的迭代分支进行开发
 git checkout -b v1.6/licl

 # 若已存在该分支则merge develop代码保证个人迭代分支代码最新
 git checkout v1.6/licl
 git merge develop
 ```
2. 开发过程中，修复一个bug或者完成一个新功能提交一个commit，并按规则写清楚commit message。

3. 每天完成各自模块的功能后提交代码，并到gitlab上发起merge request，请求合并到develop分支。

4. 转测阶段，对于简单bug可直接在个人迭代分支上修改，复杂的bug需另起分支修改。

5. 版本发布后删除个人该版本的迭代、修复分支，重新checkout下版本的迭代分支。

# message规范
- 格式： (scope) subject
- Type 和 Subject 是必填，scope(本次提交影响范围)可以省略。
- subject 英文小写，首字母也不大写。完整清晰的描述本次 commit 的提交内容。
