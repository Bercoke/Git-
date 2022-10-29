#### 优雅的提交修改

##### git commit命令详解

commit 提交修改到`本地仓库`

```shell
# -m 后面的内容是提交的信息（备注）
git commit <file1> <file2> ... -m "commit messages"
# -a 把暂存区里所有的修改都提交
git commit -a -m "message"
# 没输入-m时会打开一个vim界面输入message
git commit
# 将此次提交追加到上一次commit内容里
git commit --amend
```

---

##### /*git commit格式，git的commitizen*/

---

##### git push命令

git push用于将本地分支的更新推送到远端主机

```shell
                     源          目的
git push <远程主机名> <本地分支名>:<远程分支名>
git pull <远程主机名> <远程分支名>:<本地分支名>
# 例如
git push origin  master:refs/for/master
# 如果不写本地分支名，则表示删除指定的远程分支，表示把远程分支置空
```

---

##### git push和冲突控制

git push时如果有冲突

```shell
git pull #将分支拉下来
手动解决冲突
git commit
git push
```

---

##### git commit合并

当对一个任务多次提交时，可以将多个commit合并为一个

```shell
git rebase -i xxx  # xxx是第一个不合并的commit的hash值
```

git rebase后会出现一个文件，说明怎么合并commit

```shell
# pick 的意思是会执行这个commit
# squash 的意思这个commit会被合并到前一个commit
```

修改后保存出现下一个文件，说明怎么修改message

```shell
# 未注释掉的是包含在commit message里的
```

---

##### 查看commit的内容

```shell
-----------
git log  # 显示日志
git log --onelie # 每条日志显示一行
git log -[length] # 只显示前面的length条日志
git log --skip=[skip] - 3 # 跳过前面的skip条日志
git log -p # 显示一些统计信息以及文件的改动内容和行信息
git log --stat # 显示提交的作者、日期message和文件内容统计信息
git shortlog # 显示每个author提交commit和多少条commit
-----------  过滤
git log --after="2021-8-21" # 2021-8-21后的所有日志
git log --before="2021-8-21"

git log --author="Dounin" # 作者
git log --grep="issue" # 查看提交文本中是否包含issue的日志
git log --./src/http/modules/ngx_http_xslt_filter_moudle.c # 按文件
git log -S "ngx_free" # 按内容
------------
git show commit-id  # 显示commit-id的提交内容

```





