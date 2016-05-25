---
title: How to integrate Sublime Text 3 with Git and GitHub
date: 2016-05-24 13:00:58
tags: [Sublime Text, Git, GitHub]
---
# How to integrate Sublime Text 3 with Git and GitHub

### Step 1: Git的安装与配置

1. 从[Git官网](https://git-scm.com/)获取相应环境的安装文件并安装

2. 在Git的安装目录中打开git-bash.exe,执行以下命令：
`git config --global user.name "username"`
`git config --global user.email "username@email.com"`
运行后可以使用以下命令查看配置：
`git config -l`

3. (可选)配置push.default参数：
`git config --global push.default matching`
在sublime中使用push命令时需要配置push.default参数，在命令行中使用无需配置。
push.default参数主要设置执行push命令时的策略，主要选项有：
    * nothing: Do not push anything
    * matching: Push all matching branches (default)
    * tracking: Push the current branch to whatever it is tracking
    * current: Push the current branch

4. 在Git Bash中输入`ssh-keygen -t rsa`，执行命令后提示输入密钥文件路径和文件名，在这里使用默认(/c/Users/yourusername/.ssh/id_rsa)设置，直接按回车。然后提示输入密码，这里使用默认(即没有密码)，然后按两次回车。程序将生成的一对密钥存放在刚才设置的路径下。密钥分为私钥(id_rsa)和公钥(id_rsa.pub)。私钥保存在自己的电脑上，公钥交给项目负责人添加到服务器上。用户必须拥有与服务器公钥所配对的私钥，才能访问服务器上的代码库。
**【注意】请妥善保管私钥，私钥外泄可能导致服务器上的代码泄漏!**

### Step 2: 连接GitHub

1. 打开[GitHub](https://github.com/)主页并登录。

2. 依次选择settings > SSH and GPG keys > New SSH key，添加一个title并将id_rsa.pub中的内容(可以直接拖到sublime中打开)复制到key中，然后点击Add SSH key按钮，即可添加成功。这样就可以使用git连接GitHub了。

### Step 3(可选)： 在sublime中添加Git插件

1. 利用Package Control安装好Git插件后，依次选择Preferences > Package settings > Git > Setting - Default，将"git_command"中的false修改为cmd路径(这里用"C:/Program Files/Git/git-bash.exe")。

2. 因本人习惯使用命令行，这里就不介绍sublime中Git插件的使用方法了。

### Step 4： 在sublime中添加Terminal插件

1. 按照常规方式安装Terminal插件后，依次点击Preferences > Package Settings > Terminal > Settings – Default，为了确保插件升级后配置不丢失，建议将修改的配置都存储到Setting - User中。这里只需在Setting-User中添加以下内容即可：
`{ "terminal": "C:\\Program Files\\Git\\git-bash.exe" }`

2. 修改快捷键(个人喜好)，依次点击Preferences > Key Bindings - User，添加以下代码：
`{ "keys": ["ctrl+alt+t"], "command": "open_terminal" },`
`{ "keys": ["ctrl+shift+t"], "command": "open_terminal_project_folder" },`

### Step 5： Git试练

1. 在sublime中，新建一个工作目录，如GitTest，在该目录中新建一个文件(如index.html)并打开，输入一些内容后，打开terminal，输入`git init`来初始化环境

2. 输入`git add index.html`来添加新增或修改的文件

3. 输入`git commit -m "this is a test"`来提交

4. 在GitHub上新建一个与本地工作目录同名的仓库

5. 在terminal中输入`git remote add origin git@github.com:yourname/GitTest.git`

6. 如果执行完上条命令后出现`fatal: remote origin already exists`，则先执行`git remote rm origin`，再执行该命令

7. 输入`git pull origin master`，更新文件

8. 输入`git push origin master`，提交文件

9. 回到GitHub，刷新查看结果

### Step 6： 更多Git教程

1. [Pro Git](https://git-scm.com/book/en/v2)

2. [常用Git命令清单](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)

3. [Git教程 - 廖雪峰](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

4. [tryGit](https://try.github.io/levels/1/challenges/1)

5. [How to Use Git and GitHub](https://www.youtube.com/playlist?list=PLAwxTw4SYaPk8_-6IGxJtD3i2QAu5_s_p)