[toc]

# kafka


注意:

- git 项目使用 `git clone https://github.com/hewenyuAndroid/kafka.git` 命令下载项目时，会打包所有分支的文件，当前项目的 dev 分支文件比较大，需要跳过该分支
- 当前项目涉及的软件在 `dev` 分支
- 使用: `git clone --single-branch --branch master https://github.com/hewenyuAndroid/kafka.git` 命令，只 clone master 分支的代码，不影响拉取的速度
- 代码下载到本地后，`git fetch` 命令可以正常使用


## kafka 运行环境安装

当前虚拟机使用的是 wsl2

> jdk 配置

下载地址: https://www.oracle.com/java/technologies/downloads/#java17

```shell
# 解压 jdk 到指定目录
tar -zxvf jdk-17_linux-x64_bin.tar.gz -C /usr/local

# 配置 jdk 环境变量
export JAVA_HOME=/usr/local/jdk-17.0.7
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/
```

> kafka 配置

下载地址: https://kafka.apache.org/downloads

```shell
# 安装 kafka
tar -xzf kafka_2.13-3.7.0.tgz -C /usr/local/
cd kafka_2.13-3.7.0
```







