## Git常用命令

![image-20211124135216595](D:\桌面\收纳夹\Typora\Git\image-20211124135216595.png)

1. 设置用户签名、邮箱

2. 进入工作文件夹，打开bash

3. 初始化本地库：git init

4. 将文件保存至缓存区：git add 文件

5. 将文件从缓存区删除：git rm --cached 文件

6. 查看本地库状态：git status

7. 将暂存区文件提交到本地库：git commit -m "日志信息" 文件名

8. ![image-20211124143847320](D:\桌面\收纳夹\Typora\Git\image-20211124143847320.png)

9. 查看历史纪录：git reflog

10. 撤销工作区修改：git checkout -- readme.txt

11. git log：查看详细信息

12. * git status查看本地库是否有修改过的文件

    * 有红色的修改过的文件，git add 文件，保存至缓存区

    * 提交本地库git commit -m "second commit" hello.txt![image-20211127172945131](D:\桌面\收纳夹\Typora\Git\image-20211127172945131.png)

      新增三行，删除三行，因为是对行进行处理，会先删除原来的行，再增加新的行

    * 提交完之后，再查看本地库装态，应该是干净的

    * 查看版本信息：git reflog

    * 此时指针指向第二个版本，HEAD -> master

13. 版本穿梭
    1. 查看版本信息：git reflog，获得版本号
    2. 查看详细信息：git log
    3. 回到之前版本：git reset --hard 8a8ea9b(版本号)
    4. 文件夹中查看版本号：HEAD中查看当前指针，然后点进refs -> heads -> master查看

14. 分支操作

    1. |      命令名称       |            作用            |
       | :-----------------: | :------------------------: |
       |     git branch      |          创建分支          |
       |    git branch -v    |          查看分支          |
       | git checkout 分支名 |          切换分支          |
       |  git merge 分支名   | 把指定分支合并到当前分支上 |

    2. 查看分支：git branch -v

    3. 创建分支：git branch hot-fix

    4. 切换分支：git checkout hot-fix

    5. 修改文件内容，本地库上传

    6. 切换分支：git checkout ==master==

    7. 合并分支，先回到master分支，在master分支下进行合并：git merge 分支名

    8. 按键q可以退出显示

15. 代码冲突：当前分支与待合并分支都有代码修改![image-20211127195506728](D:\桌面\收纳夹\Typora\Git\image-20211127195506728.png)

    1. MERGING：正在合并中
    2. 手动修改代码，保留需要的部分
    3. 修改完之后要添加到暂存区
    4. 提交到本地库中不能带文件名

16. 团队协作和跨团队协作

    |              命令名称              |                           作用                           |
    | :--------------------------------: | :------------------------------------------------------: |
    |           git remote -v            |                 查看当前所有远程地址别名                 |
    |    git remote add 别名 远程地址    |                          起别名                          |
    |         git push 别名 分支         |              推送本地分支上的内容待远程仓库              |
    |         git clone 远程地址         |                将远程仓库的内容克隆到本地                |
    | git pull 远程库地址别名 远程分支名 | 将远程仓库对于分支最新内容拉下来后与当前本地分支直接合并 |

    

    1. 登录github

    2. 点击new repository

    3. 仓库名称自定义，不用担心重名，每个用户下的仓库名字随意

    4. 选择公共库或私有库

    5. HTTPS，拷贝链接

    6. 创建别名：

       1. git remote -v 查看别名
       2. 创建别名：git remote add git-demo https://github.com/lxh-12/git-demo.git
       3. 此时会出现两个别名，既可以拉取，也可以推送

    7. 推送本地库到远程库

       1. 代码上传：git push 别名 分支

          ![image-20211128102551112](D:\桌面\收纳夹\Typora\Git\image-20211128102551112.png)推送成功

    8. 拉取远程库到本地库
       1. git pull 别名 分支：git pull git-demo master 
       2. 拉取动作自动提交远程库
    9. 克隆远程库到本地
       1. 注意删除凭据管理器中的账号信息，windows之恶能同时登陆一个账号信息
       2. git clone https://github.com/lxh-12/git-demo.git，网址从code里获取![image-20211128104403328](D:\桌面\收纳夹\Typora\Git\image-20211128104403328.png)
       3. 完成了三件事：
          1. 拉取代码
          2. 初始化本地库
          3. 创建别名，需要自行进去查看别名，git remote -v
       4. 克隆只需要一个链接，push需要团队
    10. 修改代码，完成本地库推送
        1. 要将代码推送至别人的代码库，先加入lxh-12团队
        2. 登录需要推送的用户，settings -> Manage access -> 添加用户名，复制pending invite
        3. 打开个人待推送的github账户，复制打开网址，同意
        4. git push 别名 分支
        5. 完成推送
        6. push代码
    11. fork代码
        1. 可以直接搜索，用户名加上仓库名称
        2. 点击fork，将代码叉到本地，
        3. clone到本地修改，上传
        4. Pull requests,拉取请求
        5. 另一端刷新，能看到Pull requests有一个拉取请求
        6. 查看修改，同时可以相互通讯
        7. 查看完毕，merge pull合并代码

17. SSH免密登录：

    1. C:\Users\11347中有一个.ssh文件，可以删掉之前的，用指令ssh-keygen -t rsa -C lxh-12新生成一个公钥
    2. 查看公钥id_rsa.pub，复制内容
    3. 进入GitHub，点击settings->SSH and GPG keys，复制公钥
    4. 复制SSH网址，在本地pull ，可下载代码
    5. 修改，push上传

18. 













