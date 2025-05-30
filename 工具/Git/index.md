# git

文档教程

1. https://www.bootcss.com/p/git-guide/
1. https://docs.github.com/en/get-started/git-basics/managing-remote-repositories
1. https://www.w3schools.com/git/git_push_to_remote.asp


```
git init
git add .
git commit -m ""
git remote add origin [url]
git push -u origin main
```

> 解决win和linux平台换行符不匹配问题：
>
> win：git config --global core.autocrlf false

## git proxy

```bash
git config --global https.proxy http://127.0.0.1:7890
git config --global https.proxy https://127.0.0.1:7890
```



## 本地初始化

```bash
// 新建仓库
git init
// git clone
git clone /path/clone/a/repo
git clone usename@host
// 添加到缓冲区
git add <filename>
// 提交改动
git commit -m '提交信息'
// 推送
git push origin master
```



`git branch -M main`修改分支名

`git remote add origin [url]`

`git pull -u origin [远程分支](:[本地分支])`

`git pull origin [分支]`提交

```mermaid
gitGraph
   commit
   commit
   branch develop
   commit
   commit
   commit
   checkout main
   commit
   commit
```



## 信息查询

`git config --list`查询配置

`git branch`查看当前分支

`git status`仓库状态

`git log`提交记录

## .gitignore

```.gitignore
# dir 不需要提交的目录
/node_modules
​
# file 不需要提交的文件
config.ini
​
# log 不需要提交的任意包含后缀名为log的文件
*.log
​
# Package Files 不需要提交的任意包含后缀名为jar的文件
*.jar
```

`git rm --cached test.js`

>[frankiegao123](https://www.zhihu.com/people/d67b17f766b8694fe9ae0e91e4a8b538)
>
>.gitignore 前 push 了也可以忽略的，使用 git rm -r --cached . 然后 git add . 再 commit, push 就可以了。

### 本地合并多条commit

合并2条commit`git rebase -i HEAD~2`
弹出pick，将第二条及以下的pick改成s，即squash

可选操作：接着弹出一个文本，将被合并的commit信息删除或者注释掉

### git良好规范

- 频繁commit，谨慎push
