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

