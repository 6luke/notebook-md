## git使用笔记

#### 配置邮箱、用户名

```
git config --global user.name "username"
git config --global user.email useremail@example.com
```



#### git commit message

##### header

type(scope): subject

type: feat/fix/docs/style/refactor/test/chore



#### 修改远程仓库地址

```
git remote rm origin
git remote add origin url
```



#### 分支

```
查看所有分支
git branch -a

查看当前分支
git branch

切换分支
git checkout 分支名
```

