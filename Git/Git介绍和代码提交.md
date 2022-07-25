### <center> Git介绍和代码提交
#### 1.Git概述和工作流程
&emsp;&emsp;Git是分布式版本控制系统（Distributed Version Control System，简称 DVCS。
&emsp;&emsp;Git的详细命令可以参考Git官网[https://git-scm.com/docs](https://git-scm.com/docs).
**Git仓库类型**
- 本地仓库 ：开发人员在自己电脑上的仓库。
- 远程仓库：远程服务器上的仓库。

**Git三大操作**
- Clone：克隆，将远程仓库下载到本地。
- Push：推送，上传本地仓库代码到远程仓库。
- Pull：拉取，将远程仓库代码下载到本地。![在这里插入图片描述](https://img-blog.csdnimg.cn/f06db5937a274ba58f504d8e3ed6cf66.png#pic_center)

**Git提交代码**
- 1.从远程仓库Clone代码；
- 2.对代码进行修改；
- 3.提交修改的代码到本地git缓存区 
- 4.推送代码到本地git仓库
- 5.提交本地代码到远程仓库
```powershell
git clone <repositories_address> #下载代码到本地
git pull <remote_name> <remote_branch_name> #从远程主机拉取代码合并到本地分支
git add <code_name> #提交某个文件到本地git缓存区
git add . #提交所有修改到本地git缓存区
git commit -m "修改说明" #推送代码到本地git库
git push <remote_name> <remote_branch_name> #将本地remote_branch_name分支推送到远程remote_name的remote_branch_name分支上
```
**Git合并代码**
- 1.切换到需要合并的分支上
- 2.执行合并命令
- 3.解决冲突
- 4.添加到暂存区
- 5.提交到本地版本库
例如我要合并分支`heyongqi`到`main`分支上
```powershell
git checkout main #切换到main分支
git merge heyongqi #合并分支
#手动解决冲突
git add . #添加代码到暂存区
git commit -m "修改说明" #提交代码到本地库
```
#### 2.Git常用命令
**Git用户名和邮箱设置**
```powershell
git config --global user.name "username" #设置用户名
git config --global user.email "useremail" #设置邮箱
git config --global user.name #查看用户名
git config --global user.email #查看邮箱
git config --list #查看git的其他配置
```
**git分支操作**
```powershell
git branch #查看本地分支
git branch -r #查看远程分支
git branch -a #列出本地和远程所有分支
git branch <branch_name> #新建分支
git branch -d <branch_name> #删除分支
git branch -D <branch_name> #强制删除分支
git checkout <branch_name> #切换分支
git checkout -b <branch_name> #创建并切换分支
git merge <branch_name> #把branch_name分支合并到当前分支
```

