## 1 获取git仓库

​	获取git仓库有两种方式：

		- 将尚未进行版本控制的本地目录转化为Git仓库
		- 从其他服务器 clone一个已经存在的Git仓库（这里我们使用Github作为clone的仓库）

**1.1从已存在目录中初始化**

```
$ cd 目录
$ git init //创建一个.git子目录。包含初始化Git仓库必须的文件。是Git仓库的骨干
```

**1.2 从Github中clone一个已存在的仓库**

```
$ git clone link [自定义名称]
// link可以使https://协议，也可以是git://协议或者ssh传输协议
```



## 2.暂存与提交

​	目录中的每一个文件都是两种状态：

 - **已跟踪**：被纳入版本控制的文件。

   上一次快照中的记录，可能是未修改，也可能已修改或放入暂存区。

  - **未跟踪**（我们在1.1中初始化的目录中文件此时均是未跟踪状态）

​    工作目录中除了已跟踪文件都属于未跟踪文件（废话），这些未跟踪文件既不存在与上次快照的记录中，也没有没放入暂存区。

​	**(1)检查当前文件状态**

    ```
$ git status
$ git status -s(--short) 
    ```

​	第二种方式具体细节可以查看[状态简览](https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E8%AE%B0%E5%BD%95%E6%AF%8F%E6%AC%A1%E6%9B%B4%E6%96%B0%E5%88%B0%E4%BB%93%E5%BA%93)

**(2)创建文件并跟踪新文件**

	- 首先创建新文件README.md,通过git status查看仓库的状态

```
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:   
  (use "git add <file>..." to include in what will be committed)
    README
nothing added to commit but untracked files present (use "git add" to track)
```

	- 追踪文件

```
$ git add README.md
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
    new file:   README
```

	- 修改文件内容并暂存

```
修改文件内容后
此时通过git status查看状态。
（1）如果之前filename已存在于暂存区，则此时可以在to be commited和modified都可以看到该文件；to be commited（暂存区）的文件是之前add的，而not staged for commit的文件则是最新修改的
（2）如果之前filename不在暂存区，则只在modified中看到改文件
$ git add "filename"
此时最新的更改被保存到暂存区
```

 - 忽略文件	

   在.gitignore中列出我们要忽略的文件模式，具体细节可以查看[gitignore](https://github.com/github/gitignore)

- 查看已暂存和为暂存的差异

```
$ git diff   //查看当前工作区和暂存区之间的差异
$ git diff --staged   //查看暂存区和git目录(本地)的差异
```

​	可以使用图形化的工具或外部diff来查看比较差异。git difftool调用emerge或vimdiff等软件

 - 提交更新

   ```
   git commit -m "相关说明"
   ```

   注意此时要通过git status查看是否有modified但是未staged的文件。未在暂存区的文件提交不会被记录。

   跳过暂存区使用提交

   ```
   git commit -a//将所有已跟踪过的文件暂存起来一并提交
   ```

   

## 3.撤销





## 4.与远程仓库的交互





## 5 .Git别名