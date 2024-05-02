### **Git常用命令**

1. **三个工作区**
   - > 工作目录 (Working Directory)：也称为工作区，是你当前正在工作的目录，其中包含你编辑的文件。
   - > 暂存区 (Staging Area 或 Index)：是一个缓存区域，用于暂时保存你的改动。在这个区域中，你可以选择性地添加、删除或修改文件，然后提交这些更改到版本库中。
   - > 版本库 (Repository)：也称为 Git 仓库，包含项目的完整历史记录和元数据。版本库存储了所有的提交 (commits)，每个提交都包含了文件的快照以及提交时的元数据信息。

2. **文件状态**
   - > **已跟踪**: 是指那些被纳入了版本控制的文件，在上一次快照中有它们的记录，在工作一段时间后， 它们的状态可能是未修改，已修改或已放入暂存区。
   - > **未跟踪**: 工作目录中除已跟踪文件外的其它所有文件都属于未跟踪文件，它们既不存在于上次快照的记录中，也没有被放入暂存区。 
  
3. **常用命令**
   1. > 配置命令
        ```shell
        // 配置用户名
        git config --global user.name erika

        // 配置邮箱
        git config --global user.email erika@kuwo.cn
        ```
   2. > 使用命令 
        ```shell
        //查看哪些文件处于什么状态
        git status

        // 此命令比较的是工作目录中当前文件和暂存区域快照之间的差异。 也就是修改之后还没有暂存起来的变化内容。
        // 若要查看已暂存的将要添加到下次提交里的内容，可以用 git diff --staged 命令。
        git diff

        // 添加文件到暂存区
        git add .

        // 移动/重命名文件或目录
        // 在使用其他工具重命名文件时，记得在提交前 git rm 删除旧文件名，再 git add 添加新文件名。
        git mv 

        // 从暂存区删除内容
        git rm

        // 删除暂存区的文件，不影响物理磁盘文件。
        git rm --cached <file>

        // 提交更改到本地库
        git commit -m "message" 

        // 自动把所有已经跟踪过的文件暂存起来一并提交。
        git commit -a

        // 第二次提交将代替第一次提交的结果。 修补提交
        git commit --amend

        // 查看提交记录
        git log

        // 显示每次提交所引入的差异。
        // 使用 -<n> 选项来只显示最近的两次提交：
        // --stat 选项在每次提交的下面列出所有被修改过的文件、有多少文件被修改了以及被修改过的文件的哪些行被移除或是添加了。 在每次提交的最后还有一个总结。
        git log -p 
        ```

4. **分支管理**
   
   ```shell
   // 创建分支
   git branch 新分支
   
   // 创建并切换分支
   git checkout -b 新分支

   // 显示分支列表
   git branch
   // 切换分支
   git checkout 分支名

   // 合并分支
   git merge

   // 删除分支
   git branch -d 分支名
   ```

5. **远程仓库**
   
   ```shell
   // 查看远程仓库
   git remote -v

   // 添加远程仓库
   git remote add <shortname> <url>
   
   // git fetch 命令从服务器上抓取本地没有的数据时，它并不会修改工作目录中的内容。 它只会获取数据然后让你自己合并。 
   // git pull 在大多数情况下它的含义是一个 git fetch 紧接着一个 git merge 命令。
   // 抓取远程仓库
   git fetch <remote>
   
   // 推送到远程仓库
   git push <remote> <branch>

   //查看某个远程仓库
   git remote show <remote>

   // 重命名远程仓库
   git remote rename <old> <new>

   // 移除一个远程仓库
   git remote remove <name>
   ```

6. **.gitignore 的格式规范**

- 所有空行或者以 # 开头的行都会被 Git 忽略。

- 可以使用标准的 glob 模式匹配，它会递归地应用在整个工作区中。

- 匹配模式可以以（/）开头防止递归。

- 匹配模式可以以（/）结尾指定目录。

- 要忽略指定模式以外的文件或目录，可以在模式前加上叹号（!）取反。
