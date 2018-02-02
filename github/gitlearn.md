[TOC]
# 记录一下个人学习GitHub的经历
- [x]  为什么要学习GitHub？
- [ ]  GitHub入门
- [ ]  Git工具的基本使用
- [ ]  [markdown语法](../Markdown常用语法.txt)
- [ ]  git GUI工具
- [ ]  git 进阶教程
- [ ]  
## github 入门
### **.gitignore**
.gitignore 是一个纯文本文件，里面存放忽略被版本控制的文件
每行代表忽略一个文件，或一类文件，
注释： `# `所有的文字都可以算注释
直接vim .gitignore
如果想把.gitignore忽略的文件加入暂存区，可以git add -f [文件名]

可以不用自己编写自己的.gitignore
github 为我们编写了一些特定的 ![](image/ignore.png)

- 查看gitignore 忽略的规则
- git check-ignore -v [文件名]

### Git常用命令
1. git status 查看git状态
2. git log 查看本仓库的日志
3. git config --global user.name AllenLeic 修改全局配置的用户名字
4. git config --global user.email leicong2015@outlook.com 修改全局配置的用户email
5. git config -l  显示所有git config命令
6. git remote -v 查看远程仓库remote状态  

### Git配置SSH协议
- 生成SSH 协议公钥和私钥
- ssh-Keygen -t rsa -C "leicong2015@outlook.com"  
- 将用户主目录下面的 .ssh 文件夹下面id_rsa.pub 打开，把上面的key复制下来放到  
- github登陆状态的setting--> key 粘贴就行了。  
- 然后再本地git clone 或 添加 remote   
- 添加remote 格式为：git remote add origin git@github.com:AllenLeic/Java-learning-journey.git  

- 调用git remote -v 查看是否链接成功；
- 首次推送会弹出：Are you sure you want to continue connecting (yes/no)? 
- 手动输入yes，然后回车回车，确认就行了。
- 如果推送成功的话在GitHub上的登陆状态能看到之前的SSH key已经变成了绿色图标了。