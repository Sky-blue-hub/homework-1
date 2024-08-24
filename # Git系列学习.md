# Git系列学习
## 教学问题回答
- 什么是Git？
	- Git是一个免费开源的分布式版本控制系统，它使用一个叫做仓库的数据库来记录文件的变		化，仓库中的每个文件都有一个完整的版本历史记录，可以看到谁在什么时间修改了什么文件	的哪些内容，在需要的时候也可以把文件恢复到之前的某一个版本。
	- 特性：免费开源，速度快，功能强大，支持离线工作，强大的分支管理
- Git是用来干什么的？
	- 利用Git的版本控制系统，可以跟踪每个文件的变化，让项目成员之间的协作更加的高效，		Git使用的是分布式版本控制系统，每个成员都有一个完整的版本库，当需要同步时，只需要成		员之间仓库互相同步一下即可。
- Git 和 GitHub到底是什么关系？
	- 如下图所示：
	![image-20240823133354349](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240823133354349.png)
	Git编译保存到本地仓库的内容需要被推送到Remote这个远程仓库GitHub中才能被外界访问，同时，GitHub也会通过抓取和克隆本地仓库的信息，来实现对于文件的访问
	- 两者之间的联系：
		通过git clone函数可以将远程仓库中的一些内容保存到本地仓库
	- 同步过程：
		- git push :从本地仓库中传输内容到远程仓库
		- git pull:从远程仓库中推送内容到本地仓库
	
- 对于我们团队来说Git 的作用是什么？
	- 在我们团队智能车的开发管理过程中，Git的主要作用是帮助我们有效地管理和追踪代码变更。Git作为一个版本控制系统，可以帮助我们跟踪代码的每一次修改、合并和更新。通过Git，我们可以轻松地查看代码的历史记录，追踪代码的变更，并确保每个人都在使用最新的、正确的版本。此外，Git还可以帮助我们避免冲突和错误，利用它可以轻松地比较不同版本的代码的功能，快速解决任何不一致的问题。
- 如果我们团队需要使用Git协同工作，我们要怎么做？
	- 如果我们团队使用Git来协同工作，首先需要确保每个人都已经安装并熟悉了Git。然后，团队可以创建一个公开的Git仓库，以便所有人都可以访问和提交代码。团队成员可以随时将新代码提交到Git仓库，并使用pull request功能请求其他成员审核和合并。这样可以确保代码的一致性和准确性。此外，团队还可以使用Git的分支功能，以便在开发过程中进行迭代和测试。最后，定期召开团队会议，讨论代码变更、问题和解决方案，以确保团队的协同工作。

## Git的安装
- 如何检测已经安装成功
	- 在终端中输入：
	 ```
	  git -v
	 ```
	如果出现版本信息，则说明安装成功
	![image-20240821081602051](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240821081602051.png)
	
- 如何用快捷键打开终端
	- windows 系统：使用win+R,然后输入cmd进入终端
	
- Git的相关工具：（安装时附带）
	- Git GUI:Git 提供的图形界面工具
	- Git Bash：Git提供的命令行工具  

## Git的使用方式
- 命令行(推荐)
	- 特点：最基本，做常用
	- 操作过程：在终端中输入Git命令来使用Git
	- 注意事项：
		- 执行Git命令：以Git开头，后面跟上需要的操作
		- 配置模式：
			- --global：全局配置，所有仓库生效
			- --system: 系统配置，对所有用户生效
			- --省略（Local）：本地配置，只对本地仓库有效
- 图形化界面(GUI)
	- 通过专用的图形化软件来使用Git
- IDE插件/扩展
	-在常用的IDEA或者VSCODE这些工具中利用插件或者扩展使用Git

## Git的初始化配置
- 配置用户名和邮箱
	打开Git Bash
	- 设置用户信息：
        ```
        git config	--global user.name "Fan Xu"
        git config  --global user.email "2627158519@qq.com"
        ```
	- 保存用户名和密码：
		```
		git config --global credential.helper store
		```
	- 查看配置信息
		```
		git config --global user.name
		git config --global user.email
		```
		或者使用下面这种方式
		```
		git config --global --list
		```
		如下图所示
		![image-20240821102302166](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240821102302166.png)

## 目录管理
- 创建目录
	mkdir (make directories)
- 切换目录
	cd (change directory)
	
## 新建仓库
- 创建仓库的方式
	- 方式一：git init		*自己电脑上直接创建一个仓库*
		示例代码：
		```C
		mkdir learn-git		//创建一个叫做learn-git的目录
		cd learn-git		//切换到这个叫做learn-git的目录
		git init			//可以在该根目录下创建一个仓库
		ls -a				/*查找是否有一个叫做.git的目录（不能直接用ls命令来查										看，因为其是一个隐藏目录）（-a是显示所有文件，包括隐藏文件）*/
		cd. git
		ls -altr			//查看其中的文件内容
		git init my_repo    //在learn-git下面创建了一个叫做my_repo的仓库
		```
		如下图所示：
		![image-20240821110110852](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240821110110852.png)
		
	- 方式二：git clone  	*从远程服务器上克隆一个已经存在的仓库*
		示例代码：
		```
		git clone http://github.com/geekhall-laoyang/remote-repo.git //直接输入加入的																	   仓库的地址即可
		ls -ltr
		```
## Git 的工作区域和文件的状态
- Git的本地数据管理分区：
	- 工作区：电脑上的目录，在资源管理器中能够看到的文件夹
	- 暂存区：用于保存即将提交到Git仓库的修改内容
	- 本地仓库：通过 git-init命令创建的那个仓库，它包含了完整的项目历史和元数据，是Git存储代码和完整信息的主要位置
	**总的来说：工作区用于修改文件，并将其存储到暂存区中，然后将其提交到本地仓库中**
- Git中文件存在的状态
	- 未跟踪：新创建的，还未被Git管理起来的文件
	- 未修改：被Git管理起来，但是文件的内容没有发生变化
	- 已修改：已经修改了的文件，但是还没有添加到暂存区里面
	- 已暂存：已经修改，并且添加到了暂存区里面	
- 交互式界面简介
	- 通过上下左右的按键来控制光标的移动，按住字母i键进入编辑，按住esc键退出编译，最终要输入wq保存。

## Git中文件的添加和提交
- 创建仓库
	- 代码：
	```
	git init
	```
	
- 查看仓库状态
	- 代码：
	```
	git status
	```
	
- 添加到暂存区
	- 代码：
	```
	git add
	```
	- 注意：可以使用通配符来使用多个文件
- 提交
	- 代码：
	```
	git commit
	```
	- **注意：**
		**1. 需要使用-m来指定提交的信息，这个信息会被记录到仓库中，如果不指定-m这个参数那么git commit命令会进入一个交互式页面，默认会使用vim来编辑提交信息**
		**2. git commit 在提交的时候智慧提交暂存区中的文件，而不会提交工作区中的其他文件，没有保存在暂存区中的文件是不会被提交的，如下面例子中，只有file1.txt被保存在了暂存区，而file2.txt并没有仅在工作区，所以提交时只提交了file1.txt。**
	
- 完整代码示例
	- 代码:
	```
	cd learn-git
	git status							//获取最初的状态显示
	echo "这是第一个文件" >file1.txt	   //将”这是第一个文件写入file1.txt文件中
	ls									//查看文件列表
	cat file1.txt						//查看file1.txt文件
	git status							//获取此时的文件状态（file1.txt标红）
	git add file1.txt					//将这个文件添加到暂存区
	git status							//获取现在的文件状态（文件添加成功）
	```
	如下图所示：
	![/](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240821165509344.png)
	- 代码：
	```
	echo "这是第二个文件" >file2.txt
	git status
	git commit -m "第一次提交"			//注意：需要使用-m来指定提交的信息
	git status
	echo "这是第三个文件" >file.txt
	mv file.txt file3.txt			   //修改文件名称
	```
	如下图所示
	
	  ![image-20240821170501232](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240821170501232.png)

	- 代码
	```
	echo"这是第四个文件" >file4.txt
	echo"这是第五个文件" >file5.sh
	git add*.txt						//将所有后缀为txt的文件全部放到暂存区
	git status
	git add .							//将工作区的所有文件全部放到暂存区
	git status							//所有文件都保存在了暂存区
	git commit							//进入交互式界面
	git status							//获取当前各个文档的状态
	git log								//获取提交的信息（完整版)
	git log --oneline					//显示提交的信息（简洁版）
	```
	如下图所示
	
	![image-20240821172751671](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240821172751671.png)

	![image-20240821172819839](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240821172819839.png)

## 利用 git reset 回退版本
|模式				    |工作区 |暂存区|
|:------------------:|:----:|:----:|
|git reset --soft|Yes|Yes|
|git reset --hard|No|No|
|git reset --mixed|Yes|No|

- 利用 git reset --soft
	- 示例代码
	```
	cd learn-git
    git init git_reset
    echo "这是第一个文件" >file1.txt
    echo "这是第二个文件" >file2.txt
    echo "这是第三个文件" >file3.txt
    git add file1.txt
    git commit -m "第一次提交"
    git add file2.txt
    git commit -m "第二次提交"
    git add file3.txt
    git commit -m "第三次提交"
    git log
    git log --online
    //完成保存到本地库的功能
    git reset --soft c640ce7
    git log --online 
    //查看工作区
    ls
    cat file3.txt
    git ls-files
    //查看暂存区
    git status						//可以发现file3.txt是一个新增的文件，这个时候就可以对文件内容进行修改操作
   
	```
	从代码中可以看出：删到了所输的地址处，输出的地址对应的文件不会被删除。

	![image-20240821222957681](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240821222957681.png)
	实现的功能是退回到版本2，且将刚刚commit到仓库的文件退回到暂存区
	- 代码部分
	```
	git reset --hard HEAD^			//这种模式下会撤回上一级，同时，在工作区和暂存区都会删除掉记录
	ls
	git ls-files
	git reset --HEAD^				//这种模式下会撤回到上一级，其中工作区文件会被保留，但是暂存区								  内容会被删除
	```
	- 如下图所示：
	![image-20240822153248828](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822153248828.png)

	![image-20240822153338859](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822153338859.png)
	**注意：**
	1. **混合模式需要用git add将需添加的内容重新添加到暂存区，但是soft模式不需要，因为没有清空内容，hard模式的使用场景是当前真的要放弃本地修改的所有内容的时候**
	2. **hard模式慎用，因为会删除所有的修改所有内容**
	3. **如果要查看修改了哪些，可以使用git reflog,来查看操作的历史记录，然后找到误操作的版本号，然后再使用git reset 命令回溯到这个版本号即可：**
	```
	git reflog
	git reset --hard b270efb
	```

## 利用 git diff 
- 作用：
	1. 查看再工作区，暂存区，本地仓库之间的差异
	2. 查看文件在不同版本之间的差异
	3. 查看文件在不同分支之间的差异
- 用法：
	1. git diff 后面什么都不加：默认比较工作区和暂存区之间的差异内容，显示发生更改的文件和更改的详细信息

- 实际操作
	- 比较工作区和暂存区
		- 代码部分：
        ```
        cat file3.txt
        vi file3.txt			//用来更改file3的内容
        git diff				//查看工作区和暂存区之间的区别
        ```
		
		- 如下图所示：
		
        ![image-20240822155225406](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822155225406.png)
		图片中所示：第一行显示的是变更的文件名称，第二行：git会将文件的内容使用哈希算法生成一个四十位的哈希值，这里只显示了哈希值的前七位，后面的100644表示的是文件的权限。第6，7行是刚刚修改的内容，红色的表示删除的内容，绿色的表示的是增添的内容。
		    
        ![image-20240822155740660](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822155740660.png)
		在将工作区的内容保存到暂存区，再使用git diff，发现没有输出内容，表示工作区和暂存区内容一致了。
	  
	- 比较工作区和版本库(仓库)
		- 代码部分：
		```
		git diff HEAD						//追溯到版本库
		```
		- 如下图所示：
		
		![image-20240822160721028](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822160721028.png)
		由于内容没有提交到仓库中，所以工作区和版本库之间有差异
		
	- 比较当前暂存区和上次上次提交的同一个文件（暂存区和版本库）
		- 代码部分：
		```
		git diff --cached
		```
		- 如下图所示：
		![image-20240822162119340](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822162119340.png)

		可以发现，git diff(比较工作区和暂存区)，git diff HEAD（比较工作区和仓库),git diff --cached(比较暂存区和仓库)，都没有不同，说明三者一致了
		
	- 比较两个特定版本之间的差异
		- 代码部分
		```
		git log --oneline
		git diff 5af90b8 b270efb	//后面跟的是两次版本的提交ID，就可以比较两次版本的变化
		```
		或者
		```
		git diff HEAD 5af90b8			//最新的节点和上一个节点之间的比较
		```
		更加简单的方式:
		```
		git diff HEAD~ HEAD 		//HEAD~表示上一个版本，HEAD表示最新的版本
		```
		- 如下图所示：
		![image-20240822163329732](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822163329732.png)
		
		除了使用提交ID之外，还可以使用HEAD来表示当前分支的最新提交，HEAD是git中的重要概念，它指向的是git中的最新节点
		
		![image-20240822163751679](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822163751679.png)

		上面一个红色字体表示前面一个版本，后面一个绿色字体表示后面输入的一个版本
		
		![image-20240822164128142](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822164128142.png)

		- 比较两个分支之间的差异：
		
		- 用法扩展：
			- 代码部分
			```
			git diff HEAD~2 HEAD  //表示比较HEAD之前的两个版本和HEAD之间的差异
			git diff HEAD~3 HEAD file3.txt	//只会查看两次file3的差异内容
			
			```
			- 如下图所示：
			![image-20240822174106869](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822174106869.png)
			
## 删除文件
- 方式一：直接删除文件以后提交
	- 代码部分：
	```
	ls -ltr				//看一下编辑信息和版本时间
	rm file1.txt		//用rm命令在本地工作区中删除文件
	git ls-files		//这个命令可以看暂存区里面的文件
	```
	但是要注意的是，此时只是在本地工作区删除了文件，而暂存区的文件还没有删除
	可以用git add告诉git,在暂存区也需要删除掉
	```
	git add file1.txt
	```
	
	- 如下图所示：
	![image-20240822180637981](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822180637981.png)
	
- 方式二：使用git rm命令
	- 代码部分：
	```
	git  rm file2.txt	//这种方法直接删除了工作区和暂存区
	ls
	git ls-files
	git commit -m "delete file1.txt and file2.txt"//需要重新把删除内容提交一遍
	```
	- 如下图所示
	![image-20240822181623880](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822181623880.png)
	
## 忽略文件 .gitignore
- 作用：让仓库体积更小，更加干净
- 需要忽略的问价：
	- 系统或者软件自动生成的文件
	- 编译生成的中间文件和结果文件
	- 运行过程中生成的日志文件，缓存文件，临时文件
	- 涉及身份，密码，口令，密钥等敏感信息的文件
- 使用方法：提供需要忽略的文件的格式，这样就可以被自动忽略
	- 代码部分：
	```
	cd learn-git
	git init ignore			//在learn-git的文件夹下建立一个叫做ignore的文件
	cd ignore
	echo "some log">access,log
	git status
	mv access,log access.log
	echo "other log">other.log
	git status				//获取文件状态
	echo access.log >.gitignore			//忽略access.log这个文件
	cat .gitignore 			//查看忽略的文件名称
	git status				//被忽略的文件将无法看到
	git add . 
	git ls-files			//查看暂存区里面的文件
	```
	- 如下图所示：
	
	![image-20240822210015235](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822210015235.png)
	
	![image-20240822210132299](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822210132299.png)
	
	
	- 忽略所有的log文件
		- 方法一：
			用*.log来忽略所有log结尾的文件
		```
		vi .gitignore			//修改 .gitignore中的文件
		```
		在其中输入*.log
		```
		*.log
		```
		保存后退出，在界面中输入
		```
		echo "hello">hello.log
		git status
		git commit -am "test 21:09"
		git ls-files
		```
		可以看到hello.log文件被隐藏了
	- 如下图所示
	
	![image-20240822210732804](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822210732804.png)

- 保存过的文件的修改
	- 追加文件：
		```
		echo "modified" >>other.log
		git status
		git diff				//比较工作区和暂存区的区别
		```
		**声明：添加到.gitignore的文件不能是已经添加到版本库中的文件**
		更改这种文件的方法：
	```
	git rm --cached other.log		//不删除本地文件，只删除版本库，暂存区也不删除
	//git rm						不能直接使用这个文件，原因是这样子会把它同时从工作区和暂存区同时删除 即本地的文件也会									被删除
	```
	
	![image-20240822213729777](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822213729777.png)添加文件夹
	
	- 注意：如果文件夹里面只有被忽略的文件也会被是为空文件夹对待，不会被纳入版本控制
	```
	mkdir temp
	echo "hello" >temp/hello.txt		//在新建的temp文件夹中加入一个叫做hello的txt文件
	git status -s						//查看状态的简略模式写法
	```
	![image-20240822213528763](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822213528763.png)
	
	```c
	vi .gitignore					//修改gitignore的值
	```
	```
	temp/
	```
	![image-20240822214137763](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822214137763.png)
	
	出现的两个问号第一个表示暂存区的工作状态，第二个表示的是工作区的状态
	```
	git status -s
	```
	
	![image-20240822214411731](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240822214411731.png)
	其中M表示 .gitignore这个文件修改过
	```
	git add . 
	git commit -m "21:47"
	```
- .gitignore文件的匹配规则：
	- 从上到下逐行匹配，每一行表示一个忽略模式
	- 空行或者以#开头的行会被Git忽略。一般空行用于可读性的分隔，#一般用作注释
	- 使用标准的Blob模式匹配，例如：
		- * 通配任意个字符
		- ？匹配单个字符
		- 中括号[]表示匹配列表中的单个字符，比如[abc]表示a/b/c
		- 两个星号 ** 表示匹配任意的中间目录 ** 
		- 中括号可以使用短中线连接
			- 如：[0-9]表示任一数字
				 [a-z]表示任意一位小写字母
		- ！表示取反：忽略指令以外的文件或者目录，可以在模式前加上感叹号就可以了
	- 代码示例
	```python
	# 忽略所有的 .a文件
	 * .a
	# 但跟踪所有的 lib.a,即使你在前面忽略了 .a文件
	！lib.a
	# 只忽略当前目录下的T0D0文件，而不忽略subdir/T0D0
	/T0D0											//表示根目录
	#忽略任何目录下名为build的文件夹
	build/
	# 忽略doc/notes.txt ,但不忽略 doc/server/arch.txt
	doc/*.txt
	# 忽略doc/目录及所有子目录下的 .pdf文件
	doc/**/*.pdf
	```
## GitHub的使用
- SSH的配置
	- 主要代码：
	```
	ssh-keygen -t rsa -b 4096
	```
	- 注意：私钥文件：id_rsa	公钥文件：id_rsa.pub
	- 只需要配置一次，后续就不需要配置SSH了
- 克隆代码：
	- 主要代码：
	```
	git clone repo-address
	```
	- 更新内容的传递
		- git push :从本地仓库中传输内容到远程仓库
		- git pull : 从远程仓库中推送内容到本地仓库
		
	- 如下图所示：
	
	  ![image-20240823154928449](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240823154928449.png)

## 本地仓库和远程仓库之间的传输
- 远程仓库传输到本地仓库
- 本地仓库传输到远程仓库
	```
	git remote add origin git@github.com:Sky-blue-hub/test-2.git
	# origin 是远程仓库的别名
	git remote -v 			//当前仓库对应的远程仓库的别名和地址
	git branch -M main		//指定命令的名称为main
	git push -u origin main:main	//将本地的main分支和远程的main分支关联起来
	git pull			//从远程仓库中推送内容到本地仓库
	```
## 在VSCode中使用git
- 用命令行启动VSCode
    - 代码部分：
    ```
    cd learn-git 
    ls
    cd my_repo
    code .	//使用VSCode打开当前目录
    ```

## git中的分支
- 分支的好处：
	- 适合团队合作和开发管理
		- 可以在各自的分支上进行开发工作，最后再合并到主线代码中
		- 可以建立一个问题修复的分支来处理一些bug和缺陷，让主线代码仓库处于一个随时可用的比较稳定的状态，而不会影响到其他功能的开发和测试，保证了项目的正常运行和高效协作
		- 提高团队协作的效率，减少错误和冲突
- 分支的使用
	- 示例代码
	```
	mkdir branch			//创建一个叫做branch的本地文件夹
	cd branch				//进入这个文件夹
	git init				//开辟一个工作区
	echo main1 >main1.txt
	git add .
	git commit -m "main:1"
	echo main2 >main2.txt
	git add .
	git commit -m "main:2"
	echo main3 >main3.txt
	git add .
	git commit -m "main:3"
	git ls-files
	git branch				//查看分支：目前为止只有一个分支，就是main分支
	```
	可以使用git branch 后面加上分支名来创建一个新的分支,但是没有切换到这个分支上
	```
	git branch dev
	```
	- 方法一：
        - 可以使用git checkout 后面加上分支的名称来切换到不同的分支,如下面这个命令，就会切换到div分支上
        ```
        git checkout dev
        ```
	- **拓展：git checkout命令的用法**
		- **切换分支**
		- **恢复文件或者目录到之前的某一个状态**
		- **如果以外的修改了某个文件，就可以使用git checkout命令来恢复到我们修改之前的状态，如果分支名称和文件名称相同的话，会选择切换分支而非恢复文件** 
	- 方法二：
		- 使用git switch 命令，git switch命令是专门用来切换分支的
		```
		git switch master
		```
		
		![image-20240823193825665](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240823193825665.png)

		![image-20240823193844610](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240823193844610.png)

		![image-20240823193914394](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240823193914394.png)
	- 将修改合并到分支中：
		使用git merge命令将修改合并到分支中，merge后面的分支名称是将要被合并的分支。当前所在的分支就是合并后的目标分支。
		```
		git switch master
		git merge dev			//可以将dev分支合并到master分支中
		```
	- 查看分支的情况：
	```
	git log --graph --oneline --decorate --all
	```
	- 注意事项：
		- 一个分支被合并以后还是存在的,如果要删除，需要使用git branch -d命令
        ```
        git branch -d dev
        ```
		- 如果这个分支没有被合并过，如果要删除，需要输入git branch -D 命令来强制删除这个分支
		```
		git branch -D dev
		```
		
		![image-20240824141520563](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240824141520563.png)
## 解决合并分支的冲突
- 使用范围：两个分支修改了同一个文件的同一行代码，则会产生冲突
	- ** git commit -a -m "feat:1"   //可以实现提交，暂存两个操作**
	```
	git branch feat
	git switch feat
	vi main1.txt
	git commit -a -m "feat:2"
	git switch master
	vi main1.txt
	git commit -a -m "feat:3"
	git merge feat				//将feat合并到master文件中
	```
	可以发现，此时报错，原因是文件冲突
	可以用git diff显示两个冲突
	```
	git diff
	```
	可以使用 git merge --abort 这个命令来终止合并
	
## 回退和rebase
- 将不同分支中的修改内容合并到一起：Rebase
- 使用情况：
	- 在使用merge时必须要在master中进行，即相关代码为：
	```
	git switch master
    git merge dev
	```
	- Rebase操作可以在任意分支上执行
	```
	git switch dev
	git rebase master
	```
	dev分支上的文件嫁接到master上面
	```
	git switch master
	git rebase dev
	```
	master分支上的文件嫁接到dev上面 
	```
	git branch -d feat					//删除feat分支
	git checkout -b dev 244d35			//把div分支恢复过来（244d35指的是提交ID）
	```
	版本号信息可以通过下面的代码来查看：
	```
	git log --oneline --graph --decorate --all
	alias graph="git log --oneline --graph --decorate --all"  //重新定义代码的名称，将代码简略化
	
	```
	复制文件夹的命令：
	```
	cp -rf branch-demo rebase1			//Cp是专门复制文件夹的指令
	cp -rf branch-demo rebase2
	```
	应用rebase变更的命令
	```
	git switch dev
	git rebase master
	```

	![image-20240824142852662](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240824142852662.png)

	![image-20240824143411234](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240824143411234.png)
- 两种方法的优缺点：
	|方法|优点|缺点|
	|:---------------:|:-------------------------------------:|:----------------------------------------------:|
	|git merge|不会破坏原分支的提交历史，方便回溯和查看|会产生额外的提交节点，分支图比较复杂|
	|git rebase|不会新增额外的提交记录，形成线性历史，比较直观和干净|会改变提交历史，改变了当前分支branch out的节点，避免在共享分支使用|
	
## 分支管理和工作流模型

![K6K5NG_~2[L79]5TFH{UM{8](C:\Users\26271\AppData\Roaming\Tencent\QQ\Temp\K6K5NG_~2[L79]5TFH{UM{8.jpg)
- GitFlow工作流模型
	- ** 分类方式一**
		- 主线分支 （master 分支）
			- 地位：核心分支，包括了项目的核心稳定代码，应该时刻保持核心分支中的代码是可发布的，会被部署到生产环境中
			- 修改方式：不能直接修改，只能通过合并分支的方式来修改
				- 注意：每次合并分支的时候都建议重新建一个新的版本号（可以用git tag 命令来规定版本号）
				- 版本号规则：
					- 主版本：主要功能变化或者重大更新
					- 次版本：一些新的功能，改进和更新，通常不会影响现有功能
					- 修订版本：一些小的bug修复，安全漏洞补丁，通常不会改变现有功能和接口
        - 问题修复分支（hotfix分支）
            - 地位：
                - 包含了包含了项目某个问题修复的源码，用于修复线上的问题
                - 从主线分支中分出，修复完成以后合并到主线分支和开发分支中
                - 临时文件，修复完成以后会被删除
        - 开发分支（develop 分支）
            - 地位：
                - 从主线分支中分离出来，包含了项目最新开发版本的代码
                - 用于开发和测试
                - 项目的核心分支
                - 长期存在
        - 功能分支
            - 地位
                - 包含项目新功能的代码
                - 从开发分支中分离出来， 当功能分支稳定后会合并到开发分支
                - 只包含该功能的代码
        - 版本发布分支（release 分支）
            - 地位：
                - 包含了项目最新预发布版本的代码，用于测试和验证
                - 从开发分支中分离出来，代码稳定后回到主分支和开发分支中，然后会把预发布分支删除掉
	- **分类方式二：生命分支不同**
		- 主要分支：
			- 主分支，开发分支
		- 辅助分支：
			- 问题修复分支，功能分支，版本发布分支

- GitHub Flow模型
	- 使用人员：技术开发水平能力较高
	- 分支类型
		- 只有一个长期存在的主分支（可以直接部署到生产环境中）
		- 设置分支保护，禁止团队成员直接在主分支上面进行提交，团队成员可以从主分支中分离出自己的分支进行开发和测试，在本地分支提交代码，完成后，可以发送一个（Pull-Request),即拉请求，合并请求，团队成员对代码进行review评审，没有问题，即可发布并合并到主分支中。

- 工作规范：
	- 分支命名:
		推荐使用带有意义的描述性名称来命名分支
		- 如：版本号分支：v1.0.0
		-    功能性分支：feature-login-page(根据功能来命名)
		-    修复分支：  hotfix-#issueid-desc
	- 分支管理
		- 定期合并已经成功验证的分支，及时删除已经合并的分支
		- 保持合适的分支数量
		- 为分支设置合理的管理权限
## 拓展：cherry-pick命令
- 需求背景：
	- 想在某个稳定版本上，添加一个刚开发完成的版本中的功能。就可以使用 Cherry-pick 命令，将这个功能相关的 commit 提取出来，合入稳定版本的分支上。
	- 对于多分支的代码库，将代码从一个分支转移到另一个分支是常见需求。
	通常开发时分两种情况：
	- 需要将某一个分支的所有代码变动，那么就采用合并（git merge）
	- 只需要某一个分支的部分代码变动（某几个提交），这时可以采用 Cherry pick

- 使用方法
    比如下面两个分支：
    ```
         a - b - c - d   Master
             \
               e - f - g Feature
    ```
    将提交f应用到master分支：

    切换到 master 分支
    ```
    git checkout master
	Cherry pick 操作
	```
    git cherry-pick f
    上面的操作完成以后，代码库就变成了下面的样子。
	```
         a - b - c - d - f   Master
             \
               e - f - g Feature
	```
    从上面可以看到，master分支的末尾增加了一个提交f。
    git cherry-pick命令的参数，不一定是提交的哈希值，分支名也是可以的，表示转移该分支的最新提交。
	```
    git cherry-pick feature
    ```
    上面代码表示将feature分支的最近一次提交，转移到当前分支。
    
    ![image-20240824213706396](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240824213706396.png)
    
- ![image-20240824213733497](C:\Users\26271\AppData\Roaming\Typora\typora-user-images\image-20240824213733497.png)
    
-  herry-pick 支持一次转移多个提交。
    ```
    git cherry-pick <HashA> <HashB>
    ```
    上面的命令将 A 和 B 两个提交应用到当前分支。这会在当前分支生成两个对应的新提交。

    如果想要转移一系列的连续提交，可以使用下面的简便语法：
	```
    git cherry-pick A..B 
    ```
	上面的命令可以转移从 A 到 B 的所有提交。它们必须按照正确的顺序放置：提交 A 必须早于提交 B，否则命令将失败，但不会报错。

	**注意：使用上面的命令，提交 A 将不会包含在 Cherry pick 中。如果要包含提交 A，可以使用下面的语法。**
	```
    git cherry-pick A^..B 
    ```
- 代码冲突
    如果操作过程中发生代码冲突，Cherry pick 会停下来，让用户决定如何继续操作。

    - continue
        用户解决代码冲突后，第一步将修改的文件重新加入暂存区（git add .），第二步使用下面的命令，让 Cherry pick 过程继续执行。
	```
    git cherry-pick --continue
	```
	使用git cherry-pick hash_id合并代码，此时发生了冲突：
	手动改动冲突的代码
	解决代码冲突后，第一步将修改的文件重新加入暂存区（git add .），第二步使用git cherry-pick --continue命令，让 Cherry pick 过程继续执行。
	- abort
        发生代码冲突后，放弃合并，回到操作前的样子。
	- quit
        发生代码冲突后，退出 Cherry pick，但是不回到操作前的样子

