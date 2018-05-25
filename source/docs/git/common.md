title: 常见场景
---

这里列举常见场景，并给出相应解决方案

约定： 下文代码块中`${}`里面表示的是变量，具体值视情况而定，其余的都是正确可执行的命令。

## 本地提交

### 取消未暂存的修改

```sh
# 恢复单个文件
git checkout -- ${file}

# 恢复目录下所有文件
git checkout -- .
```

### 取消暂存

```sh
git reset HEAD
```

### 取消提交

```sh
git reset HEAD^1
```

或者

``` sh
# 查看提交的hash
git log
# 使用相应的hash回滚
git reset ${hash}
```

### 遗漏提交

```sh
git commit --amend
```

### 暂存修改

适用于当前功能开发并不完整，不能产生一次提交，但却要开发另外功能的场景

``` sh
git stash save '${msg}'
```

### 恢复暂存

```sh
git stash pop
```

## 分支管理

### 创建分支

```sh
git checkout -b ${branch}
```

### 根据远程分支创建分支

```sh
# 保证分支信息拉取下来
git pull
# 查看远程分支信息
git branch --remote
# 创建会追踪远程分支的本地分支
git checkout --track origin/${branch}
```

### 创建干净历史分支

```sh
git checkout --orphan ${branch}
```

## 远程仓库

### 强行推送

适用于本地开发了一段时间，最近才在代码托管平台上初始化远程仓库的场景

```sh
# 谨慎：本地master分支会覆盖远程master分支！
git push --force
```

## 其他

### 记住账号密码

```sh
# 输入下列命令后，再输入一次账号密码即可
git config --global credential.helper store
```

