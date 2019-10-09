 **stage & unstage**
      stage: 暂存区
      unstage: 工作区

 **回退 (各种情况的)**
1. 未commit之前:

```
git reset --hard HEAD^   // 把暂存区的修改回退到工作区
git checkout -- file     // 可以丢弃工作区的修改
git checkout -- .        //丢弃所有 all unstaged files
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
