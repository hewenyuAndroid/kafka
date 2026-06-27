[toc]

# kafka


注意:

- git 项目使用 `git clone https://github.com/hewenyuAndroid/kafka.git` 命令下载项目时，会打包所有分支的文件，当前项目的 dev 分支文件比较大，需要跳过该分支

- 当前项目涉及的软件在 `dev` 分支

- 使用: `git clone --single-branch --branch master https://github.com/hewenyuAndroid/kafka.git` 命令，只 clone master 分支的代码，不影响拉取的速度

- 代码下载到本地后，`git fetch` 命令可以正常使用，但是不会同步 `dev` 分支;

  

  > 如何拉取远程的 dev 分支

  

  方案1:  把 dev 加进跟踪列表（推荐，规范）

  ```shell
  # 1. 查看当前 remote 的 fetch 配置（应该只有 master）
  git config --get remote.origin.fetch
  # 输出类似：+refs/heads/master:refs/remotes/origin/master
  
  # 2. 把 dev 也加进跟踪（不会覆盖 master，是追加）
  git remote set-branches origin dev
  
  # 3. 拉取 dev 的数据
  git fetch origin dev
  
  # 4. 切到 dev（本地建一个 tracking 分支）
  git checkout dev
  ```

  

  方案2:  "去 origin 拿 dev 的数据，回来在本地建一个也叫 dev 的分支并 track 它"。一步到位，但**不会**把 dev 加进 `remote.origin.fetch`的常驻跟踪列表，以后 `git fetch`（不带参数）还是只拉 master。

  ```sh
  # 直接从远程 dev 拉下来，并在本地建 dev 分支，耗时操作
  git fetch origin dev:dev
  
  # 切过去
  git checkout dev
  ```

  

  


## kafka 运行环境安装

当前虚拟机使用的是 wsl2

### jdk 配置

下载地址: https://www.oracle.com/java/technologies/downloads/#java17

```shell
# 解压 jdk 到指定目录
# 如果解压报错: tar: jdk-17.0.7/lib: Cannot mkdir: No such file or directory
# 则需要使用 sudo 的 root 权限
tar -zxvf jdk-17_linux-x64_bin.tar.gz -C /usr/local

# 配置 jdk 环境变量
# step1: 打开环境变量配置文件
sudo nano /etc/profile
# step2: 添加环境变量配置
export JAVA_HOME=/usr/local/jdk-17.0.7
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/
# step3: 刷新环境变量
source /etc/profile
```

```shell
# 验证 wsl 的java环境
hewenyu@hewenyu:/usr/local/jdk-17.0.7$ source /etc/profile
hewenyu@hewenyu:/usr/local/jdk-17.0.7$ java -version
java version "17.0.7" 2023-04-18 LTS
Java(TM) SE Runtime Environment (build 17.0.7+8-LTS-224)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.7+8-LTS-224, mixed mode, sharing)
```


### kafka 配置

下载地址: https://kafka.apache.org/downloads

```shell
# 安装 kafka
# 如果解压失败，使用 sudo 添加 root 权限
tar -xzf kafka_2.13-3.7.0.tgz -C /usr/local/
cd kafka_2.13-3.7.0
```

解压后得到的 kafka 目录如下
```shell
hewenyu@hewenyu:/usr/local/kafka_2.13-3.7.0$ pwd
/usr/local/kafka_2.13-3.7.0
hewenyu@hewenyu:/usr/local/kafka_2.13-3.7.0$ ls -la
total 80
drwxr-xr-x  7 root root  4096 Feb  9  2024 .
drwxr-xr-x 12 root root  4096 Jun 27 01:13 ..
-rw-r--r--  1 root root 15125 Feb  9  2024 LICENSE
-rw-r--r--  1 root root 28359 Feb  9  2024 NOTICE
drwxr-xr-x  3 root root  4096 Feb  9  2024 bin
drwxr-xr-x  3 root root  4096 Feb  9  2024 config
drwxr-xr-x  2 root root 12288 Jun 27 01:13 libs
drwxr-xr-x  2 root root  4096 Feb  9  2024 licenses
drwxr-xr-x  2 root root  4096 Feb  9  2024 site-docs
```










