本markdown主要用来记录git语法的学习过程
![学习内容来源——廖雪峰](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013752340242354807e192f02a44359908df8a5643103a000#0)
# 1.创建版本库
* 新建文件夹命令——`mkdir`
* 显示仓库所在的当前目录——`pwd`

git的逻辑：没有消息就是好消息，没有返回内容即表示成功
正式的创建流程
1. 将该目录变成Git可以管理的仓库——`git init`
2. 将文件添加到仓库——`git add 文件名.后缀`
3. 将文件提交到仓库——`git commit -m "本次提交的声明"`   
-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的；可以多次add不同的文件，然后一次直接commit

# 3.远程仓库
## 3.1添加远程仓库
1. 在github上面创建一个仓库，在github主页点击"create n new repo"，填写相关信息
2. 我们根据GitHub的提示，在本地的learngit仓库下运行命令：
```
git remote add origin git@github.com:jinhaizeng/git-learning.git
```
git@github.com:jinhaizeng/git-learning.git这个内容在github仓库的ssh中直接能看到

3. 关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容；
4. 此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改；
## 3.2本地库和远程库的授权问题
[本地库和远程库的授权问题](https://blog.csdn.net/jingtingfengguo/article/details/51892864)

## 3.3add一次添加多个文件的问题

`git add -A`表示添加所有内容
`git add .` 提交被修改的和新建的文件，但不包括被删除的文件
`git add -u`表示添加编辑或者删除的文件，不包括新添加的文件


# 4. 时光穿梭
## 4.1版本回退 
* 看git更新过的版本信息 `git log`
* 回退到上一个版本 `git reset --hard HEAD^`
* 回退到上上一个版本 `git reset --hard HEAD^^`
* 回退到指定版本，比如回退到往上100个版本 `git reset --hard HEAD~100`
* 回退到指定的版本号，`git reset -- hard 版本号`，版本号一般只需要前几位就行了，不需要全的。如果回退，并且关闭了窗口，那么就回不去了，如果窗口还在，能看到版本号，就还回得去
* 如果关掉了或者关机了，可以使用`git reflog`查找操作的commit id,然后回退版本

## 4.2 工作区和暂存区
* 工作区就是你在电脑里能看到的目录
* 版本库：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。  
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，
还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。  
前面讲了我们把文件往Git版本库里添加的时候，是分两步执行的：  
第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；  
第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。  
因为我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。  
你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。    
所以，git add命令实际上就是把要提交的所有修改放到暂存区（Stage），然后，执行git commit就可以一次性把暂存区的所有修改提交到分支。  