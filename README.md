# git 新增笔记

## 一、使用ssh进行github免密登录
### 1、创建公钥和私钥
```shell
#生成 ssh-rsa 的公钥和私钥
# -t 为所使用的的算法
# -C 为备注
luo@DESKTOP-83PJLKP ~ [1]> ssh-keygen -t rsa -C 1007052116@qq.com
Generating public/private rsa key pair.
Enter file in which to save the key (/home/luo/.ssh/id_rsa):
Created directory '/home/luo/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/luo/.ssh/id_rsa
Your public key has been saved in /home/luo/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:1tL0j+qLg4fuFJKdfQuizHHbQtCC3gACpiQEDF2YOBQ 1007052116@qq.com
The key is randomart image is:
+---[RSA 3072]----+
|#E.+.            |
|Oo+. .           |
|..o o .   .      |
| . o = o + .     |
|  . = B S + .    |
|   o * * + . o   |
|    + +o. . . .  |
|     .o.o. .     |
|     oo..o+.     |
+----[SHA256]-----+
# 进入公钥和私钥的目录
luo@DESKTOP-83PJLKP ~> cd .ssh/
# 列出文件
luo@DESKTOP-83PJLKP ~/.ssh> ll
total 8.0K
# 私钥
-rw------- 1 luo luo 2.6K Feb 25 09:04 id_rsa
# 公钥
-rw-r--r-- 1 luo luo  571 Feb 25 09:04 id_rsa.pub

# 查看公钥，此公钥为要上传到github的公钥
luo@DESKTOP-83PJLKP ~/.ssh> cat id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDIYv87qLWS7iihorVhyjSaOP2Ob/yy3+HVDvwu8Qy4hdZO1ndiOi3qz54vg05Z4u+RSYi4/j70njK0s3zkdg+HHWzrZEBEzyuMAtHaqGKCnlUF7A+2pIXHK9e4o+f5ePbmLg5+Ray6i7gAMVJit7iTv659+RbAeDdnDJT0ik27XxKGptg+32yXc5BoidlV12RLEIt7vkU3PLpRkQVzCSxvgg7ckssk60PU5oMNZQ6Vtd/xwi31H3Q7hO8jGN76sp6OdKBgK8C+cH0h5Hfe8p2A/1xNjuq85g7JwfNKTa/1oCw0uddGyA2RMUUa2LfNm8Jx/UfNs5CnYwotzrv9DLVqZaKva4gHurEJniHNDDMvyCsIgGTbomMBKLgop93cYJOAPnlSbuFrDn3/0RQBdkqZ8DabTrVXUq+a94jaN7ew8IVcmzfHV0SeIO3+YMUMpk7/laK1xyDvHgKMoGUWEhOHciZKaaUYVvyG672H6FPff9yFkRWsIl+8ASp0dMPYHjE= 1007052116@qq.com
luo@DESKTOP-83PJLKP ~/.ssh>
```


### 2、将创建的 私钥 上传到 github
> https://github.com/settings/keys
> 点击， New SSH Key

### 3、之后就可以快乐的使用免密验证了，前提是使用的 ssh，而不是 https


## 二、git 全局配置 git ignore
```shell
# 在任意目录下创建一个 .gitignore 文件（文件名可以随意）
luo@DESKTOP-83PJLKP ~> echo .idea > .gitignore
# 查看内容
luo@DESKTOP-83PJLKP ~> cat .gitignore
.idea
# 打开 git 的配置文件
luo@DESKTOP-83PJLKP ~> vi .gitconfig


[user]
        email = 1007052116@qq.com
        name = luo
# 添加以下内容，包含刚刚的 配置文件
[core]
        excludesfile=/home/luo/.gitignore

# 之后使用 git 命令就能全局生效了        
```
