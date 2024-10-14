# git学习
## 常用命令
```js
git init
// 查看状态
git status
git diff
// 查看提交历史
git log
// 查看命令历史
git reflog

// 回退到上一个版本
git reset --hard HEAD^
// 回退到当前版本的前两个版本
git reset HEAD^^ 
// 回退到当前版本的前100个版本
git reset HEAD~100
// 如果增加--hard参数会重置工作区和暂存区，未提交的变更将被不可逆的丢弃

// 撤销暂存区的修改，重新放回工作区
git reset HEAD README.md

// 撤销某一个文件的修改
git checkout -- README.md

// 添加到暂存区
git add  README.md

// 提交
git commit -m "first commit"

// 推送
git push

```

## 知识点
leangit是git工作区，.git是版本库.
.git里面index叫暂存区

HEAD ：指向当前分支


## git学习地址
+ [ 廖雪峰git教程 ](https://liaoxuefeng.com/books/git/branch/create/index.html)
+ [git知识大全](https://gitee.com/help/categories/43)
+ [Pro Git 中文版 码云](https://gitee.com/progit/)
+ [learnGitBranching](https://github.com/pcottle/learnGitBranching)

