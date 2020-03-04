## git_test基本操作

### 新建git工作区
**mkdir 文件夹名字;**

**cd 文件夹名字**

### 新建文件
**使用记事本，typora等编辑源码文件，可用vi/vim/gedit等文本编辑器（输入：wq保存退出**

### 工作区初始化
**git init (生成.git文件夹)**

### 用户配置
**git config --global user.name “用户名”**

**git config --global user.email “用户邮箱”**

**git config -l（查看当前生效的配置）**

### 状态检测
**git status（会显示当前工作区内未被添加未被保存到文件）**

**git diff 文件名（对比修改内容）**

**git log -g/git reflog（查看版本历史记录）+ git reset --hard HEAD@{from git reflog}（前进未来某个版本）/git reset --hard HEAD^（回退上一个版本,同理加^）

### 添加文件 
**git add 文件名（添加文件至缓存区）**

**git add . （全部添加）**

### 备份文件添加评论（快照，暂存）
**git commit –m “评论内容”**

### 撤销缓存区版本修改
**git reset HEAD 文件名**

**git checkout --文件名（让这个文件回到最近一次 git commit 或 git add 时的状态，用版本库里的版本替换工作区里的版本）**

### 获取远程repository的地址，以.git结尾
**在个人github主页新建repository，并复制连接，ssh和https都可以，以.git结尾**

### 与远程repository建立连接
**git remote add origin 地址**

### 拉取远程repository的README.md文件
**git pull –rebase origin master**

### 上传本地文件到远程repository
**git push origin master**

### 从远程仓库克隆
**git git@github.com:your-name/repo-name.git**

### PS
**如果出现不能和远程仓库建立连接的报错，如下：**
> Please make sure you have the correct access rightsand the repository exists 或Permission denied (publickey).

**ssh-keygen -t rsa -C “your@email.com”**

**回车直至：**

The key’s randomart image is:

+—[RSA 2048]—-+

| ==++. . |

| . ++.o . .|

| ..o++Oo |

+—-[SHA256]—–+

**在/home/richardurben/.ssh路径下产生：**

id_rsa（私钥）

id_rsa.pub（公钥）

**gedit id_rsa.pub**

**复制到：[个人主ssh和gpg keys文件夹下](https://github.com/settings/keys)**

**验证：ssh -T git@github.com 

**可看见：**
> You’ve successfully authenticated, but GitHub does not provide shell access.
