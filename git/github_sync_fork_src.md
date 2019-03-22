# Github - 同步更新 fork 提交

## 1. 首先查看自己的远程仓库设置的情况

```bash
$ git remote -v
origin  xxxx.git (fetch)
origin  xxxx.git (push)
```

## 2. 添加 fork 的上游仓库

```bash
$ git remote add upstream yyyy.git
$ git remote -v # 查看添加后的仓库情况
origin  xxxx.git (fetch)
origin  xxxx.git (push)
upstream yyyy.git (fetch)
upstream yyyy.git (push)
```

## 3. 从新添加的仓库更新代码

```bash
git fetch upstream
```

## 4. 合并到当前的 master 上

```bash
git merge upstream/master
```

## 5. 提交代码到远程仓库

```bash
git push
```

## 6. 删除远程仓库

```bash
git remote remove upstream
```