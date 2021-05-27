## git_远程仓库 Github


本地仓库六行配置
```
git config --global user.name 你的英文名
git config --global user.email 你的邮箱
git config --global push.default simple
git config --global core.quotepath false
git config --global core.editor "code --wait"
git config --global core.autocrlf input
```

本地仓库基本操作
```
git add选择要提交的内容
.gitignore 文件描述不提交的内容
git commit -v 用来提交
git log 用来查看历史
git reset --hard xxxxxx用来切换版本
git reflog 用来查看所有历史
git branch x 创建分支x
git checkout 切换分支
git merge 合并分支
git status -sb 查看文件冲突
```


生成ssh key 
```
ssh-keygen -t ed25519 -C "your_email@example.com"
运行 ssh-keygen -t rsa -b 4096 -C 你的邮箱
cat ~/.ssh/id_rsa.pub 得到公钥。粘贴到GitHub
```

上传代码
```
添加远程仓库地址
git remote add origin git@xxxxx
推送本地master分支到远程origin的master分支
git push -u origin master
```

上传其他分支
```
方法一
git push origin x:x
方法二
git checkout x
git push -u origin x
```

下载别人的代码
```
git clone git@xxxx[目标路径]
cd 目标路径
git add/git commit/git pull/git push
```

如何下载某个分支
```
先下载整个仓库，然后git checkout 分支名
```

git clone
```
git clone git@?/xxx.git
会在当前目录下创建一个xxx目录
xxx/.git是本地仓库
git clone git@?/xxx.git yyy
会在本地新建yyy目录
git clone git@?/xxx.git .
不会新建目录，使用当前目录容纳代码和.git，最好是空目录
```

git 高级操作(了解)
```
touch ~/.bashrc
echo 'alias ga="git add"'>> ~/.bashrc
echo 'alias gc="git commit -v"'>> ~/.bashrc
echo 'alias gl="git pull"'>> ~/.bashrc
echo 'alias gp="git push"'>> ~/.bashrc
echo 'alias gco="git checkout"'>> ~/.bashrc
echo 'alias gst="git status -sb"'>> ~/.bashrc
source ~/.bashrc
```