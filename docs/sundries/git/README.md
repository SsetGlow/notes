
# Git学习

## 小命令

**1.-m** ‘’**//** 添加注释

**2.git tag <tag_name> //**创建标签

**3.git tag //**查看标签

**4.git push origin <tagname> //**推送一个本地标签

**5.git push origin --tags //**推送全部未推送过的本地标签

**6.git tag -d <tagname> //**删除一个本地标签

**7.git push origin :refs/tags/<tagname> //**删除一个远程标 ****签

**8.git log //** 查看提交日志

**9.git reset - -hard head^** (或者是版本号 **// 1094a** 这样的) **//**回退版本 ****上一个版本 **head^** 上上个版本**head^^** 或者 **head~n** （上**n**个版本）

**10.git checkout - - //**撤销修改**/**删除

**11.git rm <filename> //**删除文件

**12.git config - -global** [**user.name**](**http://user.name/**) **"**要修改的用户名**" //**修改用户名字

**git config - -global** [**user.**](**<http://user.name>**)**email "**要修改的邮箱**" //**修改邮箱

**13.git branch --set-upstream-to <branch-name> origin/<branch-name> //**本地分支与远程分支关联。

## 远程库

**1.new repository**

**2.git remote add origin <**地址**>**

**3.git push -u origin <**分支名**>**(第一次，可将两个库关联)

**git push origin <**分支名**>**(非第一次)

**4.**下载网上库：

**git clone <**地址**>**

**git clone -b <**分支**> <**地址**>**

**5.git checkout -b <**分支名**> origin/<**分支名**> //**本地**clone**多分支

**6.git rebase//**使提交成为一条线

**//**拉取远程库中指定分支

**7.git pull origin**(主机名) **master**(分支名)

**8.**查看远程库信息：

**​ git remote -v**

### 本地修改完后提交修改信息以及上传代码：

**1.git init**

**2.**本地操作

**3.git add <file>**

**4.git commit -m** ‘注解’

**5.git push**(同上)

## 分支

**1.git checkout -b <**分支名**> = git branch <**分支名**> //**创建分支

**+git checkout <**分支名**> //**切换分支

**2.git branch //**查看当前分支

**3.**对当前分支进行操作

**4.git merge <**操作的分支名**>**

**5.git branch -d/-D <**分支名**> //**删除分支**. -D** 强行删除

**6.**出现冲突时**git status** 可查看 **cat <**文件名**>** 也可查看

[**7.vi**](**http://7.vi/**) **<**冲突的文件名**>** 进入修改 ****冲突通过**>>>**以及**<<< =====** 标记出来

**8.git merge —no-ff -m "" <**分支名**> //**普通合并，可看出曾经做过合并，否则不能

**9.git stash //**储存工作区，可进行其他分支工作

**10.git stash pop //**继续工作

### git分支强行覆盖

**git reset --hard origin/**“**branch**”

### 冲突

从远程**pull**下来后 **本地合并 **然后再往远程库推送。解决冲突。