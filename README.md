Git is a distributed version control system.
Git is free software distributed under the GPL.

```js
git init
// 添加到暂存区
git add  README.md
// 提交
git commit -m "first commit"
git status
git diff
// 查看提交历史
git log
// 查看命令历史
git reflog

// 回退到上一个版本
git reset --hard HEAD^

// 撤销暂存区的修改，重新放回工作区
git reset HEAD README.md
  
  // 撤销某一个文件的修改
git checkout -- README.md
```

leangit是git工作区，.git是版本库.
.git里面index叫暂存区

HEAD ：指向当前分支

