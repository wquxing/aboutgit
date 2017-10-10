关于Git的一些知识学习记录：
git add filename:添加文件到仓库，可添加多个，如git add file1.txt file2.txt
git commit -m "ps":提交文件到仓库
git cat filename：该命令可查看文件内容；
git status :查看仓库状态，会告诉我们有没有哪些文件被修改过，以及是否有提交修改。
git diff :查看有哪些地方被修改过了。
git log :查看我们从最近到最远提交的日志，使用git log --pretty=oneline可以输出更简洁的格式。
git reset --hard HEAD^ 回退到上一个版本，git reset --hgard HEAD^^为回退到上上个版本，以此类推，100个版本写100个^比较容易数不过来，所以写成HEAD~100。
git reset --hard ******(版本号) :回到指定版本，如果不知道要回到版本的版本号，可以使用git reflog查看我们使用过的命令。
git reflog ：用来记录我们的每一次命令。
git log --graph --pretty=format:'%h -%d %s (%cr)' --abbrev-commit --reflog ：可以查看到reset后的历史，其中(HEAD -> master)指向的是当前的版本。
git diff HEAD -- filename.txt :以查看工作区和版本库里面最新版本的区别。
git diff :是工作区(work dict)和暂存区(stage)的比较.
git diff --cached :是暂存区和分支的比较.

git checkout -- filename.txt :该命令为把文件在工作区的修改全部撤销，这里有两种情况：
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
总之，就是让这个文件回到最近一次git commit或git add时的状态。

git reset HEAD file.txt :可以把暂存区的修改撤销掉（unstage），重新放回工作区.git reset命令既可以回退版本，也可以把暂存区的修改回退到工作区。当我们用HEAD时，表示最新的版本。

rm filename :在工作区删除文件

git rm filename :在版本库删除文件，删除后记得git commit

git checkout -- filename 当工作区的文件被误删之后，如果版本库当中还有，可以使用这个命令恢复被误删的文件。注意，如果使用rm删除本地文件并且使用commit提交之后，则无法再回复了，只能使用git checkout HEAD -- filename回退到之前的版本，再使用git checkout的方法恢复。

关联远程库后，第一次推送master的时候使用命令：git push -u origin master,以后每次提交只要有必要，就可以使用 git push origin master命令推送最新的修改.