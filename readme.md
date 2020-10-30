
````
git init
git add .
git commit -m "first commit"
git remote add origin https://github.com/Ysnsn/butterfly-source.git
git branch -M main
git push -u origin main
````

Github提交更新的代码

````
git status   #查看更改了哪些文件的代码
git add .   #git add 你想要提交的更改的文件 或者 git add . 所有的文件；
git branch -m 'text'   #git commit -m ‘提交信息’把本地仓库暂存区的文件提交到本地仓库
git push -u origin main   #把本地仓库中的文件同步到远程仓库中，即 git push origin main/你的分支 。
````