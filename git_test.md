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

**git log -g/git reflog（查看版本历史记录）**
**git reset --hard HEAD@{from git reflog}（前进未来某个版本）/git reset --hard HEAD^（回退上一个版本,同理加^）**

### 分支（多人协作）
1. 查看分支: git branch
2. 创建分支: git branch <name>
3. 切换分支: git checkout <name>
4. 创建+切换分支: git checkout -b <name>
5. 合并某分支到当前分支: git merge <name>
6. 删除分支: git branch -d <name>
  
### 添加文件 
**git add 文件名（添加文件至缓存区）**

**git add . （全部添加）**

### 备份文件添加评论（快照，暂存）
**git commit –m “emoji表情 评论内容”**

**git tag -a 版本号标签（如v0.0）编号（from git log --oneline）（给某个缓存区内的版本加标签)**

**git tag -d 版本号标签（删除本地标签）**

**git push origin --delete tag <版本号标签>（删除远程仓库标签）**

**常见表情标签表：**

| emoji| emoji 代码| 	commit 说明|
| :---:| :----: | :----: |
| :art: (调色板) | :art: | 改进代码结构/代码格式 |
| :zap: (闪电) :racehorse: (赛马) | :zap: :racehorse: | 提升性能 |
| :fire: (火焰) |	:fire:	| 移除代码或文件 |
| :bug: (bug) | :bug: | 修复 bug |
| :ambulance: (急救车)	| :ambulance: |	重要补丁 |
| :sparkles: (火花) | :sparkles: | 引入新功能 |
| :memo: (备忘录) | :memo: | 撰写文档 |
| :rocket: (火箭)	| :rocket: | 部署功能 |
| :lipstick: (口红) | :lipstick: | 更新 UI 和样式文件 |
| :tada: (庆祝) | :tada: | 初次提交 |
| :white_check_mark: (白色复选框) | :white_check_mark: | 增加测试 |
| :lock: (锁) | :lock: | 修复安全问题 |
| :apple: (苹果) | :apple: | 修复 macOS 下的问题 |
| :penguin: (企鹅) |  :penguin:  | 修复 Linux 下的问题 |
| :checkered_flag: (旗帜) | :checkered_flag:  | 修复 Windows 下的问题 |
| :bookmark: (书签) | :bookmark: | 发行/版本标签 |
| :rotating_light: (警车灯) | :rotating_light: | 移除 linter 警告 |
| :construction: (施工)  | :construction: | 工作进行中 |
| :green_heart: (绿心) |  :green_heart: |  修复 CI 构建问题 |
| :arrow_down: (下降箭头) | :arrow_down: | 降级依赖 |
| :arrow_up: (上升箭头) | :arrow_up: | 升级依赖 |
| :construction_worker: (工人) | :construction_worker: | 添加 CI 构建系统 |
| :chart_with_upwards_trend: (上升趋势图) |:chart_with_upwards_trend: | 添加分析或跟踪代码 |
| :hammer: (锤子)	 | :hammer:	 | 重大重构 |
| :heavy_minus_sign: (减号) | :heavy_minus_sign: | 减少一个依赖 |
| :whale: (鲸鱼) | :whale: | Docker 相关工作 |
| :heavy_plus_sign: (加号) | :heavy_plus_sign: | 增加一个依赖 |
| :wrench: (扳手) | :wrench: | 修改配置文件 |
| :globe_with_meridians: (地球) | :globe_with_meridians: | 国际化与本地化 |
| :pencil2: (铅笔) | :pencil2: | 修复 typo |

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

**git push origin --tags（共享标签）**


### 从远程仓库克隆
**git clone git@github.com:your-name/repo-name.git**

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

### example（同步更新Github Fork的项目）
1. fork项目并clone到本地
2. 进入项目根目录
3. 添加remote指向上游仓库
~~~ git
git remote add upstream https://github.com/用户/项目名称.git
~~~
4. 把上游项目fetch下来
~~~ git
git fetch upstream
~~~
5. merge到master
~~~ git
git checkout master
git merge upstream/master
~~~
6. push到自己的远程仓库

## github上的fork同步操作
pull new requests -> compare changes -> switching the base -> create pull requests(title) -> back to your pull requests -> merge pull request -> confirm merge.
