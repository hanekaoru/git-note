## 安装 / 初始化

放在最前面，使用 ```git help log / add / commit...``` 可以查看相关命令的操作方式

----

安装完成后首先需要设置用户和地址

```js
git config --global user.name "name"

git congig --global user.email "email"
```

然后新建一个文件夹用作 git 仓库，再初始化这个 git 仓库

```js
git init  // 初始化

pwd  // 显示当前目录

ls   // 显示当前目录文件
``` 

然后添加文件到 git 仓库

```js
git add 文件名  // 添加文件，可以反复添加多次

git commit -m "描述"  // 提交文件到仓库
```


#### 附录 git add 的各种区别:

```js

git add -A   // 添加所有改动

git add *     // 添加新建文件和修改，但是不包括删除

git add .    // 添加新建文件和修改，但是不包括删除

git add -u   // 添加修改和删除，但是不包括新建文件


// 在 commit 前撤销 add:

git reset <file> // 撤销提交单独文件

git reset        // unstage all due changes

// add / commit 前撤销对文件的修改:

git checkout -- README.md  // 注意, add添加后(同 commit 提交后)就无法通过这种方式撤销修改

```




## 查看工作区状态

使用

```js
git status  // 查看工作区状态
```

如果出现如下警告：

```js
warning: CRLF will be replaced by LF in readme.txt.
The file will have its original line endings in your working directory.
```

可以使用：

```js
git config core.autocrlf false
```

至于出现原因，详细见：[git如何避免”warning: LF will be replaced by CRLF“提示？](https://www.zhihu.com/question/50862500)

提交前的时候可以查看具体修改了哪些内容，使用：

```
git diff
```


## 版本回退

可以使用 git log 命令来查看历史记录

```js
git log
```

如果感觉输出信息太多，可以使用 --pretty=oneline 参数（使其一行显示）

```js
git log --pretty=oneline
```

回退到上一个版本，使用 reset 命令

```js
git reset --hard HEAD^
```

如果回退到前两个版本，可以使用 HEAD^^ 或者 Head~2，依次类推

```js
git reset --hard Head^^

git reset --hard HEAD~2
```

如果回退版本后，在使用 git log 后就查看不到之前最新版本的信息了

这个时候可以使用下面命令指定回到之前某个版本（4cda21 这个就是之前使用 git log 查看的版本号，只需要前面几位即可，git 会去自动查找）

```js
git reset --hard 4cda21
```

但是如果找不到之前的版本号，可以使用下面命令来查看提交过的每一次命令

```js
git reflog
```

小小总结：

* 回退　/ 更新 到指定的版本，使用 ```git reset --hard commit_id```

* 回退前，使用 ```git log``` 查看提交历史，确定回退版本

* 向跳转到指定版本，使用 ```git reflog``` 查看历史提交记录，确定跳转版本
