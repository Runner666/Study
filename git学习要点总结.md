**git常用命令:**

git config --global user.name "Your Name"   
git config --global user.email "email@example.com"  
git config --global core.editor emacs(编辑器名，默认通常为Vim)  
git config --list 查看所有配置  
git config <user.name> 查看某一项配置  
git init 在当前文件夹创建git仓库  
git add 文件名 添加文件  
git add . 将所有工作区的文件添加到暂存区  
git <add> --help 查看add的所有命令  
git commit -m "提交说明"  
git commit -a -m "提交说明" 跳过git add <filepath>直接提交，即直接从工作区进入git仓库  
git status :查看仓库当前状态  
git diff:查看修改的内容  
git log:查看3次提交记录  
git reset --hard HEAD^(或者 HEAD~1)  
Ctrl+c:结束继续输入  
git reflog:查看命令历史  
git rm <filepath> 移除版本库中已跟踪的文件，并连带从工作目录中删除该文件  
git rm --cached <filepath> 从版本库中移除，但保留在磁盘中（即不再跟踪该文件）  
git checkout <filepath> 恢复用rm 删除且没有提交的文件，不可恢复用git rm <filepath>删除的文件  

将本地仓库与远程仓库连接起来:  
1.生成SSH key:ssh-keygen -t rsa -b 4096 -C "自己注册时的邮箱"  
2.启动ssh-agent:eval $(ssh-agent -s)(默认情况下是启动的)  
3.在github上添加新的SSH key:Title任意填，  
用clip < ~/.ssh/id_rsa.pub复制key，然后粘贴到Key区域  
4.关联远程仓库:git remote add wx(给远程仓库起一个连接名，默认origin) git@github.com/houtu/News.git  
5.git push -u origin master:将本地仓库暂存区的内容推送到远程仓库中(github上)，实际上是将本地仓库的master分支推送到远程，因为第一次推送时远程仓库是空的，所以用-u参数，当远程仓库非空时就不需要用-u参数了。
注：当本地仓库只关联一个远程仓库时，可以直接用git push 向远程仓库推送内容  

从远程仓库复制内容:  
git clone git@github.com:houtu/News.git  
从远程仓库clone内容不需要与远程仓库建立关联关系

git pull: 更新当前分支

创建分支:  
git checkout -b 分支名(该命令将创建分支和切换分支融合在了一起)  
git branch:查询所有分支，当前分支前有一个*  
git checkout master:转换到master分支，在该分支上融合新分支git merge 分支名  
删除不需要的分支:git branch -d 分支名

在分支上打标签:  
首先切换到需要打标签的分支，git tag 标签名  
git tag:查看所有标签  
git show 标签名:查看标签信息  
git tag -a 标签名 -m "说明信息":打一个带说明的标签  
git tag -d 标签名:删除不需要的标签

可以通过fork将别人开源的项目添加到自己的仓库中

上传本地内容到GitHub上的步骤：  
1)在GitHub上建一个仓库（Create new pro）  
2)将本地文件夹变成本地厂库（git init）  
3)将本地文件里的内容（准仓库内容）添加到本地仓库的master分支上（git add 文件名）   
4)提交以上操作（git commit -u "提交说明"）  
5)将本地仓库与远程仓库连接起来（git remote add origin git@github.com:houtu/News.git）  
（该命令说明：远程仓库的名字是origin，以后每次向远程仓库推送只需用orgin即代替了远程仓库的具体URL）  
6)推送本地内容到远程仓库（git push -u origin master）  

本地Java原码管理注意：  
我们获得了一份JAVA工程源码，在本地我们需要用eclipse来进行开发，eclipse会为项目生 成.classpath .project .settings等eclipse特有的文件（夹），
还会自动编译源码，产出的.class文件放在bin目录下。这几个文件和bin文件夹，都没必要进行控制，因为他们会自动生成，不同的开发环境和编译环境的产出
并不相同，我们只需把src目录下所有东西用git管理起来就行。
在这种情况下，我们可以创建一个名为 .gitignore 的文件，列出要忽略的文件模式

Git 有三种状态，你的文件可能处于其中之一：  
已修改（modified）、已暂存（staged）和已提交（committed）。  
已修改表示修改了文件，但还没跟踪，如新增的文件和刚修改过的文件。  
已暂存表示对一个已修改文件的当前版本做了标记（git add）。  
已提交表示数据已经安全地保存在本地数据库中(git commit)。  
由此引入 Git 项目的三个工作区域的概念：工作目录、暂存区域以及Git仓库。

[廖雪峰git学习教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
