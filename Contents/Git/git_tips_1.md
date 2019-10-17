 **关键词**
    
stage: 暂存区  
unstage: 工作区  
branch： 分支 ()  
HEAD:  

 **回退 (各种情况的)**
1. 未commit之前:

```
git reset --hard HEAD^   // 把暂存区的修改回退到工作区
git checkout -- file     // 可以丢弃工作区的修改
git checkout -- .        //丢弃所有 all unstaged files
git stash                //把所有修改的丢到垃圾桶中
```

2. 已commit 但是没有push:
```
 git reset e12d8ef^        //每一個 ^ 符號表示「前一次」的意思, 如果
 git reset --mixed         // default, Commit 拆出來的檔案會留在工作目錄
 git reset --soft HEAD^    // Commit 拆出來的檔案會直接放在暫存區
 git reset --hard HEAD^    // 檔案都會丟掉,如果想找回之前丢弃的commit 使用 git reflog 找到之前那个commit hash code 
```

3. 已commit & push:  git revert

```
git revert HEAD  // revert最近一次commit
```

reset 和 revert 区别: revert 会改变历史记录

**特别小技巧**

1. skip git commit hooks 跳过提交时的检查
```
git commit --no-verify     //-n:  bypasses the pre-commit and commit-msg hooks
```

2. clear git cache; 针对 .gitignore 需要忽略但是已经存在于项目当中的文件
```
git rm -r --cached .
```

3. git 对比两个分支差异
```
git log master..dev   //查看dev比master多提交哪些
```

4. git-bisect  定位bug 


几个使用场景：
1. 当A,B已经分别提交了
