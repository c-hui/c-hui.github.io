---
title: Java开发大师-开发环境搭建
date: 2020-03-28 22:18:50
tags: Java
---

环境搭建方法和软件均来自[张哥](https://github.com/pepstack)，非常感谢！

# Windows 环境搭建

## 安装软件

### Java 8

下载地址：
- 官网：[oracle download](https://www.oracle.com/java/technologies/javase-downloads.html)
- 百度网盘：[Java 8
](https://pan.baidu.com/s/1Qx0M7mrqdcZZXztOuEb5Qw) ，提取码：`maib`

安装目录：`C:\DEVPACK\JAVA\jdk1.8.0_162`

### maven
下载地址：
- 官网：[apache download](https://maven.apache.org/download.cgi)
- 百度网盘：[maven](https://pan.baidu.com/s/1oKDHUyXfOZF6MDvfJ2lIdA)，提取码：`kams`

解压目录：`C:\DEVPACK\apache-maven-3.3.3`

### VSCode

下载地址：
- 官网：[visualstudio](https://code.visualstudio.com/)
- 百度网盘：[VSCode](https://pan.baidu.com/s/1CgtQauJKISBNf-Slo05SVw)，提取码：`p6bq`

### VSCode Java 插件

下载地址：
- 官网：[vscode-java-installer](http://aka.ms/vscode-java-installer-win)
- 百度网盘：[vscode-java-installer](https://pan.baidu.com/s/1SnrxejFv5XCWG3jUyNwNYQ)，提取码：`zllw`

### GIT
下载地址：
- 官网：[git](https://git-scm.com/downloads)
- 百度网盘：[git](https://pan.baidu.com/s/1UTwDvLvBjqORA74XCC-2ww )，提取码：`zfth`

## 配置环境变量

配置系统的环境变量

```
_DEVPACK_=C:\DEVPACK
JAVA_HOME=%_DEVPACK_%\JAVA\jdk1.8.0_162
JAVA_TOOL_OPTIONS=-Dfile.encoding=UTF8
JRE_HOME=%JAVA_HOME%\jre
MAVEN_HOME=%_DEVPACK_%\apache-maven-3.3.3
MAVEN_OPTS=-Xms256m -Xmx512m -Dfile.encoding=UTF-8
CLASSPATH=.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar
Path=(原有内容);%JAVA_HOME%\bin;%JRE_HOME%\bin;%MAVEN_HOME%\bin
```

# Ubuntu 环境搭建

建议使用阿里云服务器，搭建好环境后，随时可以开发。

## Java 8

```shell
apt install openjdk-8-jdk
```

## maven

```shell
apt-get install maven
```

## git
```shell
apt-get install git
```

## VSCode

可以使用本地 VSCode 的 remote-ssh，连接上我们的云服务器，远程安装 Java 开发插件。

## 配置环境变量

```shell
vim /etc/profile
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export JRE_HOME=${JAVA_HOME}/jre
export JAVA_TOOL_OPTIONS='-Dfile.encoding=UTF8'
export MAVEN_OPTS='-Xms256m -Xmx512m -Dfile.encoding=UTF-8'
export CLASSPATH=.:${JAVA_HOME}\lib\dt.jar:${JAVA_HOME}\lib\tools.jar
source /etc/profile
```

# 验证

新建一个目录 `Workspace` 存放项目。

```shell
java -version
mvn -version
mkdir Workspace
cd Workspace
mvn archetype:generate -DarchetypeCatalog=internal -DarchetypeArtifactId=maven-archetype-quickstart -DgroupId=com.github.hellomvn -DartifactId=hellomvn -Dpackage=com.github.hellomvn -Dversion=1.0
cd hellomvn/
mvn test
mvn clean package
java -cp target/hellomvn-1.0.jar com.github.hellomvn.App
```