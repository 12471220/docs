# GIT
## git常用命令
### git merge
1. `git merge <branch>`：将`<branch>`分支合并到当前分支。
2. `git merge --abort`：取消合并，恢复到合并前的状态。
3. `git merge --continue`：解决完冲突后继续合并。
4. `git merge --no-ff`：禁用快进合并，强制创建一个新的分支并保留合并历史。
    ```
    A --- B --- C  (main)
       \
        D --- E  (feature)
    ```
    变成
    ```
    A --- B --- C --- F  (main)
       \        /
        D --- E  (feature)
    ```
5. `git merge --squash`：将多次提交合并为一次提交，并且历史不可见，并且不可溯源（慎用！！！）。
    ```
    A --- B --- C  (main)
       \
        D --- E  (feature)
    ```
    变成
    ```
    A --- B --- C --- F  (main)
    ```
    其中，`F`是`D`和`E`的合并，但是`D`和`E`的历史不可见。
6. `git merge --strategy`：指定合并策略。
   - `git merge --strategy=ours`：保留当前分支的所有内容，忽略合并分支的内容。
   - `git merge --strategy=theirs`：保留合并分支的所有内容，忽略当前分支的内容。

### git branch
1. `git branch`：查看分支。
2. `git branch <branch>`：创建分支。
3. `git branch -d <branch>`：删除分支。
4. `git branch -D <branch>`：强制删除分支。
5. `git branch -m <new_branch>`：重命名分支。
6. `git branch -a`：查看所有分支（包括远程分支）。
7. `git branch -r`：查看远程分支。

### git remote
1. `git remote add <name> <url>`：添加远程仓库。
2. `git remote rm <name>`：删除远程仓库。
3. `git remote -v`：查看远程仓库。
4. `git remote show <name>`：查看远程仓库详细信息。
5. `git remote update`：更新远程仓库。
6. `git remote prune <name>`：删除远程仓库分支。