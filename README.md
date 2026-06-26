[toc]

# kafka


1、当前分支是项目涉及的软件
2、切换分支，下载软件到本地后，文件夹里面的文件是分卷压缩的产物
3、分卷压缩的文件解压后，需要去掉文件后面的 .1 后缀，即可达到完整的文件


注意:

- git 项目使用 git clone path 命令下载项目时，会打包所有分支的文件，当前项目的 dev 分支文件比较大，需要跳过该分支
- 使用: `git clone --single-branch --branch master https://github.com/hewenyuAndroid/kafka.git` 命令，只 clone master 分支的代码
- 代码下载到本地后，git fetch 命令可以正常使用






