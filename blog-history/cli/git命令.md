---
title: git 命令
date: 2019-11-24 13:12:09
---

## 在本地使用

查看变动 

```sh
git status -sb
```

> `git status -sb` 是什么意思：git status 是用来显示当前的文件状态的，哪个文件变动了，方便你进行 git add 操作。-sb 选项的意思就是，-s 的意思是显示总结（summary），-b 的意思是显示分支（branch），所以 -sb 的意思是显示总结和分支。 

查看历史变动

```sh
git log
```

总结

1. git init，初始化本地仓库 .git
2. git status -sb，显示当前所有文件的状态
3. git add 文件路径，用来将变动加到暂存区
4. git commit -m "信息"，用来正式提交变动，提交至 .git 仓库
5. 如果有新的变动，我们只需要依次执行 git add xxx 和 git commit -m 'xxx' 两个命令即可。别看本教程废话那么多，其实就这一句有用！先 add 再 commit，行了，你学会 git 了。
6. git log 查看变更历史

克隆

```sh
git clone git@github.com地址
```

## 上传更新

在本地目录有任何变动，只需按照以下顺序就能上传：

1. `git add 文件路径`
2. `git commit -m "信息"`
3. `git pull` （）
4. `git push`

下面是例子

1. `cd git-demo-1`
2. `touch index2.html`
3. `git add index2.html`
4. `git commit -m "新建 index2.html"`
5. `git pull`
6. `git push`

## 防止其他文件上传

在项目目录创建 `.gitignore` 文件就可以指定「哪些文件不上传到远程仓库」，比如

`.gitignroe` 文件示例：

```
/node_modules/
/.vscode/
```

> 这样就可以避免 `node_modules/` 和 `.vscode/` 目录被上传到 github 了。

## 其他

还有一些有用的命令

- `git remote add origin git@github.com:xxxxxxx.git` 将本地仓库与远程仓库关联
- `git remote set-url origin git@github.com:xxxxx.git` 上一步手抖了，可以用这个命令来挽回
- `git branch` 新建分支
- `git merge` 合并分支
- `git stash` 通灵术
- `git stash pop` 反转通灵术
- `git revert` 后悔了
- `git reset` 另一种后悔了
- `git diff` 查看详细变化