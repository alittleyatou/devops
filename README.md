# devops
客户或产品有新的需求变更，或者测试人员提出bug时，在jira上创建issue，开发人员得到通知，对dev分支做修改，每个项目会有不同的分支。

分支中会包含一个名叫docker的目录，里面包含了将整个项目的build输出（对于java的web应用来说就是war文件）打包成docker image所需要的文件。

开发人员提交代码并push到Gitlab，Gitlab触发Web Hook，通知Jenkins项目有新的变更。Jenkins收到通知，从Gitlab pull代码并自动启动编译构建。

如果构建成功调用docker的目录下脚本来生成docker image并push到私有docker仓库上。

通过chef，通知最终的部署节点，下载最新版image,删除正在运行的容器，以新image来启动容器，完成项目的更新。整个过程会在短短几分钟就能看到结果。

# 有容云参考资料：
【有容云】PPT | 容器与CICD的遇见
https://www.cnblogs.com/youruncloud/p/6214886.html
