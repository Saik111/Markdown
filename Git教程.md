# Git Bash的简单实用教程

## 本地文件的基本操作

进入某一个文件夹，和Linux系统一样有两种方式：

1. 直接进入该文件夹位置，然后右键Git Bash Here，在当前文件夹打开Git Bash，类似于打开Terminal，此时的终端的路径就是在当前文件夹，然后对文件进行相关操作
2. 在桌面右键Git Bash Here，通过dir查看当前目录文件，通过cd命令进入文件夹，通过cd ..命令返回上一级，也可以使用cd xxx/xxx/xxx一次性直接到达指定位置，通过rm指令删除指定文件（注意在Git Bash中，使用cd命令是‘/’而不是Windows系统中的‘\’）
3. 可以通过pwd命令来查看当前是在哪个文件夹进行的操作

```git
users@LAPTOP MINGW64 /d/Git (master)
$ pwd
/d/Git
```

## 将文件夹变成本地仓库

进入到指定的文件夹之后，使用git init指令将本地文件夹变成本地仓库

```git
git init
```

你会发现原来的文件路径后面多出一个（master）

本地文件夹中也会出现.git隐藏文件夹（是git的控制文件），千万不可以删除

![Alt text](https://pic1.zhimg.com/80/v2-ab6b3664031ff05368e129581f897f2c_720w.webp)

## 添加文件

我在文件夹中复制进去了自己的一个测试代码的文件，然后使用如下指令

```git
git add 文件名.文件类型
```

**敲黑板！！！**肯定有好奇宝宝和我一样，文件既然已经放进了仓库的问价中，为什么还要用git add指令去添加呢。可以理解为将此文件交给git去管理。

git文件有四种状态，1. untracked files、2. change to be commited、3. nothing to commit, working directory clean、4. changes not staged for commit。

对于同一个文件既有change to be committed 又有 change not staged for commit，说明文件在add后进行了修改，如果这时候直接执行commit, add过后进行的修改不会修改到仓库，文件的状态会变为第四个4. changes not staged for commit，如果这时候执行add，然后在commit,这样add后的修改也会一起提交到仓库。我们平时使用git的时候一般都是2，3，4不断的循环，现在假设Git中没有add命令会怎么样呢？我们会发现只会有三个状态1，3，4，少了状态2,4，我们只需要在3,4两个状态间循环就可以。也许你会说这不是很好嘛，简单了很多，但是往往复杂的设计是为了带来更多的功能。

有了git add 命令，你可以在随时add，如果代码出现了问题，可以随时倒回到git add 时候的状态。你还可以随时比较当前代码和git add 时代码的差别，git add 时和仓库代码的差别，当前代码和仓库代码的差别。

![Alt text](https://pic1.zhimg.com/80/v2-915fd9f6a4cfcb5a9d72ab87275d6094_720w.webp)

也可以用以下指令进行批量操作

```git
git add -A     提交所有变化
git add -u     提交被修改的文件和被删除的文件，不包括新文件
git add .      提交新文件和被修改的文件，不包括被删除的文件
```

## 提交文件

```git
git commit -m  "修改注释"
```

一定要commit，否则无法同步到云端

```git
users@LAPTOP MINGW64 /d/Git (master)
$ git commit -m "第二次修改"
[master 5b477e8] 第二次修改
 1 file changed, 7 insertions(+), 1 deletion(-)
```

查看修改内容

```git
git diff 文件名.文件类型
```

查看所有文件内容

```git
cat 文件名.文件类型
```

## 同步远程仓库

### 新建仓库

首先在GitHub新建一个仓库，新建仓库的流程如图所示

![Alt text](https://pic4.zhimg.com/80/v2-8719f48615f142b950b5f73a0a85f40b_720w.webp)
![Alt text](https://pic4.zhimg.com/80/v2-eda2245aa13905620f4e82ee51721833_720w.webp)

然后会弹出一个界面，里面有不同的连接方式，选择ssh方式进行连接

![Alt text](https://pic4.zhimg.com/v2-de015a30bb9aea93b16be837abf08d67_r.jpg)

也可以选择用HTTPS进行传输，不过速度会很慢

其中origin是仓库的代名词，也可以换成其他的，但是自己要记住

```git
要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git；
关联后，使用命令git push -u origin master第一次推送master分支的所有内容；
此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；
要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。
Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。
```

### 将新仓库和本地git相关联

```git
git remote add origin git@github.com:PanXF-HUST/test.git
```

复制代码到Git Bash，即可实现新仓库和这个的相关联

使用 git remote -v 命令查看关联状况

```git
git remote -v
```

![Alt text](https://pic4.zhimg.com/80/v2-e0f5e65367606ce5c930b8cc0bede7cf_720w.webp)

我为了测试把仓库代称改成别的名字在这里换成了test

如果不想与这个远程仓库连接了，只需要用git remote remove test即可删除连接，重新连接就可以恢复

### 内容同步

在第一次同步的时候，必须使用如下指令

```git
git push -u 仓库代称 master
```

第一次推送master分支时，必须加上-u参数，git不但会推送分支，还会把本地master分支与远程master分支相关联，以后的推送直接使用git push 仓库代称 master即可

```git
git push 仓库代称 master
```

同步后可以进GitHub的web端看已经被修改

## 远程仓库修改后更新本地仓库

### 克隆仓库

```git
git clone 复制的SSH或者HTTPS key
```

在团队合作中，你的队友修改了远程仓库之后，你如何确保自己的文件跟远程仓库一致呢，这就需要以下步骤了。在你init或者Clone的过程中，Git会自动在本地分支与远程分支之间，建立一种追踪关系(tracking)。比如，在git clone的时候，所有本地分支默认与远程主机的同名分支，建立追踪关系，也就是说，本地的master分支自动连接到远程的origin/master分支。

### 取回远程文件

```git
git pull 仓库代名称
```

我在GitHub的web端修改了文件及修改了文件名，取回远程文件

