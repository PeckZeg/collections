Git 环境搭建
============

## 生成公钥

使用 git 服务需要在本地生成一个 ssh 公钥，你可以使用 `ssh-keygen` 生成，也可以通过 [`Git for Windows`](https://msysgit.github.io/) 所附带的功能来生成。

### 使用 ssh-keygen 生成公钥

（坑）

### 使用 Git for Windows 生成公钥

安装了 `Git for Windows` 之后，打开 `Git Gui`，选择 `帮助` → `Show SSH Key`，如果你之前没有生成过 SSH 公钥，那么窗口中的 `Generate Key` 是一个可点击的按钮，你只需要猛击它就能自动生成一个 SSH Key，当然，你之前有生成过的话，窗口中会显示你的公钥。

将生成的 `id_rsa.pub` 文件拷贝到远端的 `/tmp` 文件夹之下，以备使用。

## 架设远端服务器

### 创建 git 用户

最好的情况是建立一个 `git` 用户组，再往里面添加用户，不过现在只有我一个人在使用就忽略了这个可选项。在远端服务器的终端中，使用下列命令以创建一个 git 用户（此处用户名为 `peckzeg`），并在 `/home/peckzeg` 目录下建立一个存放公钥的 `.ssh` 文件夹。

```
sudo adduser peckzeg
su peckzeg
cd ~
mkdir .ssh
```

### 配置 ssh 公钥

```
cat /tmp/id_rsa.pub >> ~/.ssh/authorized_keys
```

### 创建一个仓库

```
mkdir project
cd project
mkdir project.git
git --bare init
```

使用 `--bare` 参数初始化的 git 仓库是不带任何目录的（这当然是我们所期望的）。

## 配置本地仓库

推荐使用 `Git Bash` 而不是直接使用 `Git Gui` 配置本地仓库。

假设我们要将本地仓库存放于 `E:\project`

```
cd e:
mkdir project
cd project
git init
git add .
git commit -m 'init'
git remote add origin `用户名@git服务器:/home/peckzeg/project/project.git`
git push origin master
```

至此，已经把本地仓库设置完毕，接下来你就可以使用 `Git Gui` 来方便的操作 git 仓库了

## 参考

* [git服务器的简单搭建](http://blog.chinaunix.net/uid-16979052-id-3491746.html)
* [搭建Git服务器](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137583770360579bc4b458f044ce7afed3df579123eca000)