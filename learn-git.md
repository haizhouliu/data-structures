* git init (初始化,把目录变成Git可以管理的仓库) 
  - .git 文件夹内保存着每次更改的版本
* git add . ( 把文件从工作目录添加到暂存区stage)
* git add file -p (一次大的修改分批次add)
* git status (查看工作目录和暂存区改变的文件的状态)
  - 当 当前分支、暂存区、工作目录的文件内容一致时,会显示working tree clean
* git commit  -m "first commit"  (把暂存区文件提交到当前分支)
* git log (版本提交日志/记录)
* git show commit-id(版本号) (显示此次提交的具体信息)
* git diff (对比工作区文件和暂存区文件之间的差异)
* git diff --cached (默认对比暂存区文件和上一次固化版本之间的差异)
* git commit -a -m "update file" (合并add,commit命令.适用于add过的文件)
* git rm file (删除工作区文件，并且添加到了暂存区)
* 撤销修改
- git restore file.txt (未add,直接丢弃工作区file文件的修改)
  - git reset HEAD file.txt (已add,未commit,丢弃 已添加到暂存区 的修改)
- git restore --staged file.txt (新版Git命令，功能同上)

- 版本回退

  - git reset --hard 版本号 (当已commit,回退到指定版本号)
- git reflog (查看每一次commit版本号)

- 配置密码
  - git config --global credential.helper cache

- 查看关联的远程分支
  - git remote -v

- 将本地master分支与远程仓库地址绑定
  - git push -u origin(远程仓库地址) master

- 修改当前所在分支名
  - git branch -M xxx

- 克隆线上内容到本地
  - git clone https://github.com/xxx (本地master分支就是由线上origin的master创建的,已关联)