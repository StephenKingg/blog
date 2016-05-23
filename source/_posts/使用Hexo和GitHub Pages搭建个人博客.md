# 使用Hexo和GitHub Pages搭建个人博客
### Step 1: 创建仓库
&emsp;&emsp;在GitHub中新建两个repository，分别命名为`username.github.io`和`blog`。前者用于存放deploy之后产生的文件，后者用于存放Hexo源文件。这里需要说明的是：<br>
&emsp;&emsp;1. GitHub Pages有两种类型：User/Organization Pages 和 Project Pages。<br>
&emsp;&emsp;2. 用于存放User Pages的仓库必须使用username.github.io的命名规则，而Project Pages没有特殊要求。<br>
&emsp;&emsp;3. User Pages将使用仓库的master分支，而Project Pages将使用gh-pages分支。<br>
&emsp;&emsp;4. User Pages通过http(s)://username.github.io进行访问，而Project Pages通过http(s)://username.github.io/projectname进行访问。<br>
&emsp;&emsp;详细内容请访问[GitHub Pages Basics](https://help.github.com/articles/user-organization-and-project-pages/)。<br>
### Step 2: 安装Hexo
&emsp;&emsp;1. 安装Hexo之前，请确保计算机中已安装`Git`和`Node.js`，并且已配置了相应GitHub账号的ssh-key，可以参考我的教程：[How to integrate Sublime Text 3 with Git and GitHub](https://github.com/StephenKingg/StudyNotes/blob/master/git-github-sublime.md)。<br>
&emsp;&emsp;2. 执行以下命令即可完成Hexo的安装：<br>
&emsp;&emsp;&emsp;&emsp;`npm install hexo-cli -g`<br>
### Step 3: 搭建本地Hexo博客
&emsp;&emsp;1. 在本地新建一个文件夹(例如D:\blog)，进入该文件夹，鼠标右击选择Git Bash Here，输入`hexo init`，该命令会在目标文件夹中建立网站所需要的所有文件。<br>
&emsp;&emsp;2. 在Git Bash中输入`npm install`，安装依赖包。这样我们就搭建起了本地Hexo博客。在Git Bash中输入`hexo server`，然后在浏览器中输入`http://localhost:4000/`，即可在本地浏览。<br>
### Step 4: 将Hexo部署到GitHub
&emsp;&emsp;1. 打开该文件夹下的_config.yml文件，找到：<br>
&emsp;&emsp;&emsp;&emsp;`deploy:`<br>
&emsp;&emsp;&emsp;&emsp;`type:`<br>
&emsp;&emsp;&emsp;作以下修改：<br>
&emsp;&emsp;&emsp;&emsp;`deploy:`<br>
&emsp;&emsp;&emsp;&emsp;`type: git`<br>
&emsp;&emsp;&emsp;&emsp;`repo: git@github.com:username/username.github.io.git`<br>
&emsp;&emsp;&emsp;&emsp;`branch: master`(User Pages为master， Project Pages为gh-pages)<br>
&emsp;&emsp;2. 执行以下命令，安装deploy插件：<br>
&emsp;&emsp;&emsp;&emsp;`npm install hexo-deployer-git --save`<br>
&emsp;&emsp;3. 执行以下命令，即可完成部署：<br>
&emsp;&emsp;&emsp;&emsp;`hexo d -g`<br>
&emsp;&emsp;4. 在浏览器中输入`username.github.io`进行浏览。<br>
### Step 5: 更改Hexo的主题
&emsp;&emsp;1. 如果想使用其它主题，可以在Git Bash中执行以下命令：<br>
&emsp;&emsp;&emsp;&emsp;`git clone git@github.com:someone/theme-name themes/theme-name`<br>
&emsp;&emsp;2. 然后打开_config.yml文件，将`theme: landscape`修改为`theme: theme-name`，然后在Git Bash中执行以下命令：<br>
&emsp;&emsp;&emsp;&emsp;`hexo clean`<br>
&emsp;&emsp;&emsp;&emsp;`hexo d -g`<br>
&emsp;&emsp;3. 在浏览器中刷新页面看看效果~<br>
&emsp;&emsp;4. 关于Hexo主题的配置，请参考其它教程，这里就不详述了。<br>
### Step 6: 将Hexo源文件上传到GitHub
&emsp;&emsp;在Git Bash中依次执行以下命令：<br>
&emsp;&emsp;&emsp;&emsp;`git init`<br>
&emsp;&emsp;&emsp;&emsp;`git remote add origin git@github.com:username/blog.git`<br>
&emsp;&emsp;&emsp;&emsp;`git add -A`<br>
&emsp;&emsp;&emsp;&emsp;`git commit -a`<br>
&emsp;&emsp;&emsp;&emsp;`git pull origin master`<br>
&emsp;&emsp;&emsp;&emsp;`git push origin master`<br>
&emsp;&emsp;这样就完成了文件上传。这里需要注意的是，clone下来的主题文件夹中(如themes/xxx/)，如果有`.git`目录，请先删除该目录，然后执行以上命令，否则该主题中的文件无法上传。<br>
### Step 7: 在另一台计算机中同步Hexo博客
&emsp;&emsp;1. 安装Git和Node.js，并配置GitHub账号的ssh-key。<br>
&emsp;&emsp;2. 任意选择一个文件夹，使用Git Bash执行以下命令：<br>
&emsp;&emsp;&emsp;&emsp;`git clone git@github.com:username/blog.git`<br>
&emsp;&emsp;&emsp;&emsp;`cd blog/`<br>
&emsp;&emsp;&emsp;&emsp;`npm install hexo-cli -g`<br>
&emsp;&emsp;&emsp;&emsp;`npm install`<br>
&emsp;&emsp;&emsp;&emsp;`npm install hexo-deployer-git`<br>
&emsp;&emsp;&emsp;&emsp;`hexo clean`<br>
&emsp;&emsp;&emsp;&emsp;`hexo d -g`<br>
&emsp;&emsp;这样就完成了Hexo的同步。<br>
### Step 8: 日常改动
&emsp;&emsp;1. 建议先检查更新，将本地文件更新至最新版本：<br>
&emsp;&emsp;&emsp;&emsp;`git pull`<br>
&emsp;&emsp;2. 然后执行新建、修改等操作。<br>
&emsp;&emsp;3. 操作完成后，将文件同步至GitHub：<br>
&emsp;&emsp;&emsp;&emsp;`git add xxx`<br>
&emsp;&emsp;&emsp;&emsp;`git commit -m "descriptions"`<br>
&emsp;&emsp;&emsp;&emsp;`git push origin master`<br>
&emsp;&emsp;3. 然后再执行Hexo的生成文件和部署命令：<br>
&emsp;&emsp;&emsp;&emsp;`hexo d -g`<br>
### Step 9: 关于Hexo
&emsp;&emsp;关于Hexo的更多内容请访问[Hexo官网](https://hexo.io/)。<br>