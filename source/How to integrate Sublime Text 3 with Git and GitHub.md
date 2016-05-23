#How to integrate Sublime Text 3 with Git and GitHub 
###Step 1: Git的安装与配置
1.&ensp;从[Git官网](https://git-scm.com/)获取相应环境的安装文件并安装<br>
2.&ensp;在Git的安装目录中打开git-bash.exe,执行以下命令：<br>
&emsp;&emsp;&emsp;`git config --global user.name "username"`<br>
&emsp;&emsp;&emsp;`git config --global user.email "username@email.com"`<br>
&emsp;运行后可以使用以下命令查看配置：<br>
&emsp;&emsp;&emsp;`git config -l`<br>
3.&ensp;(可选)在sublime中使用push命令时需要配置push.default参数，在命令行中使用无需配置。<br>
&emsp;&emsp;push.default参数主要设置执行push命令时的策略，主要选项有：<br>
&emsp;&emsp;&emsp;nothing: Do not push anything<br>
&emsp;&emsp;&emsp;matching: Push all matching branches (default)<br>
&emsp;&emsp;&emsp;tracking: Push the current branch to whatever it is tracking<br>
&emsp;&emsp;&emsp;current: Push the current branch<br>
&emsp;&emsp;这里我们手动设置成默认值：<br>
&emsp;&emsp;&emsp;`git config --global push.default matching`<br>
4.&ensp;在git-bash中执行以下命令：<br>
&emsp;&emsp;&emsp;`ssh-keygen -t rsa`<br>
&emsp;&emsp;执行命令后提示输入密钥文件路径和文件名，在这里使用默认(/c/Users/yourusername/.ssh/id_rsa)设置，直接按回车。提示输入密码，这里使用默认(即没有密码)，然后按回车，再次确认。<br>
&emsp;&emsp;程序将生成的一对密钥存放在刚才设置的路径下。密钥分为私钥(id_rsa)和公钥(id_rsa.pub)。私钥保存在自己的电脑上，公钥交给项目负责人添加到服务器上。用户必须拥有与服务器公钥所配对的私钥，才能访问服务器上的代码库。<br>
**&emsp;&emsp;【注意】请妥善保管私钥，私钥外泄可能导致服务器上的代码泄漏!**
###Step 2: 连接GitHub
1.&ensp;打开[GitHub](https://github.com/)主页并登录<br>
2.&ensp;依次选择settings > SSH and GPG keys > New SSH key，添加一个title并将id_rsa.pub中的内容(可以直接拖到sublime中打开)复制到key中，然后点击Add SSH key按钮，即可添加成功。这样就可以使用git连接GitHub了。<br>
###Step 3(可选)： 在sublime中添加Git插件
&emsp;&emsp;利用Package Control安装好Git插件后，依次选择Preferences > Package settings > Git > Setting - Default，将"git_command"中的false修改为cmd路径(这里用"C:/Program Files/Git/git-bash.exe")。<br>
&emsp;&emsp;因本人习惯使用命令行，这里就不介绍sublime中Git插件的使用方法了。
###Step 4： 在sublime中添加Terminal插件
1.&ensp;按照常规方式安装Terminal插件后，依次点击Preferences > Package Settings > Terminal > Settings – Default，为了确保插件升级后配置不丢失，建议将修改的配置都存储到Setting - User中。这里只需在Setting-User中添加以下内容即可：<br>
&emsp;&emsp;&emsp;`{ "terminal": "C:\\Program Files\\Git\\git-bash.exe" }`<br>
2.&ensp;修改快捷键(个人喜好)，依次点击Preferences > Key Bindings - User，添加以下代码：<br>
&emsp;&emsp;&emsp;`{ "keys": ["ctrl+alt+t"], "command": "open_terminal" },`<br>
&emsp;&emsp;&emsp;`{ "keys": ["ctrl+shift+t"], "command": "open_terminal_project_folder" },`<br>
###Step 5： Git试练
1.&ensp;在sublime中，新建一个工作目录，如GitTest，在该目录中新建一个文件(如index.html)并打开，输入一些内容后，打开terminal，输入`git init`来初始化环境<br>
2.&ensp;输入`git add index.html`来添加新增或修改的文件<br>
3.&ensp;输入`git commit -m "this is a test"`来提交<br>
4.&ensp;在[GitHub](https://github.com/)上新建一个与本地工作目录同名的repo<br>
5.&ensp;在terminal中输入`git remote add origin git@github.com:yourname/GitTest.git`<br>
6.&ensp;如果执行完上条命令后出现`fatal: remote origin already exists`，则先执行`git remote rm origin`，再执行该命令<br>
6.&ensp;输入`git pull origin master`，更新文件<br>
7.&ensp;输入`git push origin master`，提交文件<br>
8.&ensp;回到GitHub，刷新查看结果<br>
###Step 6： 更多Git教程
1.&ensp;[Pro Git](https://git-scm.com/book/en/v2)<br>
2.&ensp;[常用Git命令清单](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)<br>
3.&ensp;[Git教程 - 廖雪峰](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)<br>
4.&ensp;[tryGit](https://try.github.io/levels/1/challenges/1)<br>
5.&ensp;[How to Use Git and GitHub](https://www.youtube.com/playlist?list=PLAwxTw4SYaPk8_-6IGxJtD3i2QAu5_s_p)<br>