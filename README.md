[toc]

# kafka



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







