# 使用Hexo和GitHub Pages搭建个人博客

### Step 1: 创建仓库
1. 在GitHub中新建两个repository，分别命名为`username.github.io`和`blog`。前者用于存放deploy之后产生的文件，后者用于存放Hexo源文件。这里需要说明的是：
    * GitHub Pages有两种类型：User/Organization Pages 和 Project Pages。
    * 用于存放User Pages的仓库必须使用username.github.io的命名规则，而Project Pages没有特殊要求。
    * User Pages将使用仓库的master分支，而Project Pages将使用gh-pages分支。
    * User Pages通过http(s)://username.github.io进行访问，而Project Pages通过http(s)://username.github.io/projectname进行访问。

2. 详细内容请访问[GitHub Pages Basics](https://help.github.com/articles/user-organization-and-project-pages/)。

### Step 2: 安装Hexo
1. 安装Hexo之前，请确保计算机中已安装`Git`和`Node.js`，并且已配置了相应GitHub账号的ssh-key，可以参考我的教程：[How to integrate Sublime Text 3 with Git and GitHub](https://stephenkingg.github.io/)。

2. 执行以下命令即可完成Hexo的安装：
`npm install hexo-cli -g`

### Step 3: 搭建本地Hexo博客
1. 在本地新建一个文件夹(例如D:\blog)，进入该文件夹，鼠标右击选择Git Bash Here，输入`hexo init`，该命令会在目标文件夹中建立网站所需要的所有文件。

2. 在Git Bash中输入`npm install`，安装依赖包。这样我们就搭建起了本地Hexo博客。在Git Bash中输入`hexo server`，然后在浏览器中输入`http://localhost:4000/`，即可在本地浏览。

### Step 4: 将Hexo部署到GitHub
1. 打开该文件夹下的_config.yml文件，找到：
`deploy:`
`type:`
作以下修改：
`deploy:`
`type: git`
`repo: git@github.com:username/username.github.io.git`
`branch: master`(User Pages为master， Project Pages为gh-pages)

2. 执行以下命令，安装deploy插件：
`npm install hexo-deployer-git --save`

3. 执行以下命令，即可完成部署：
`hexo d -g`

4. 在浏览器中输入`username.github.io`进行浏览。

### Step 5: 更改Hexo的主题
1. 如果想使用其它主题，可以在Git Bash中执行以下命令：
`git clone git@github.com:someone/theme-name themes/theme-name`

2. 然后打开_config.yml文件，将`theme: landscape`修改为`theme: theme-name`，然后在Git Bash中执行以下命令：
`hexo clean`
`hexo d -g`

3. 在浏览器中刷新页面看看效果~

4. 关于Hexo主题的配置，请参考其它教程，这里就不详述了。

### Step 6: 将Hexo源文件上传到GitHub
1. 在Git Bash中依次执行以下命令：
`git init`
`git remote add origin git@github.com:username/blog.git`
`git add -A`
`git commit -a`
`git pull origin master`
`git push origin master`

2. 这样就完成了文件上传。这里需要注意的是，clone下来的主题文件夹中(如themes/xxx/)，如果有`.git`目录，请先删除该目录，然后执行以上命令，否则该主题中的文件无法上传。

### Step 7: 在另一台计算机中同步Hexo博客
1. 安装Git和Node.js，并配置GitHub账号的ssh-key。

2. 任意选择一个文件夹，使用Git Bash执行以下命令：
`git clone git@github.com:username/blog.git`
`cd blog/`
`npm install hexo-cli -g`
`npm install`
`npm install hexo-deployer-git`
`hexo clean`
`hexo d -g`
这样就完成了Hexo的同步。

### Step 8: 日常改动
1. 建议先检查更新，将本地文件更新至最新版本：
`git pull`

2. 然后执行新建、修改等操作。

3. 操作完成后，将文件同步至GitHub：
`git add xxx`
`git commit -m "descriptions"`
`git push origin master`

4. 然后再执行Hexo的生成文件和部署命令：
`hexo d -g`

### Step 9: 关于Hexo
* 关于Hexo的更多内容请访问[Hexo官网](https://hexo.io/)。