### git 仓库和服务器搭建

---

#### 仓库

仓库：用git管理的一个目录，这个仓库的所有文件的改动（增/删/改）都由git跟踪记录。

##### 创建仓库

```shell
# 创建一个空的仓库git_test
mkdir git_test
cd git_test
git init
```

![image-20221027125805471](D:\0voice\git\git仓库和服务器搭建.assets\image-20221027125805471.png)

```shell
# .git目录下有很多关于git管理的文件
# 不要随意修改
```

![image-20221027130019878](D:\0voice\git\git仓库和服务器搭建.assets\image-20221027130019878.png)

```shell
# 在仓库里新建文件，此时文件不会被跟踪
# 使用如下命令查看文件状态
git status
```

![image-20221027134644038](D:\0voice\git\git仓库和服务器搭建.assets\image-20221027134644038.png)

##### 将文件添加到暂存区

把文件添加到暂存区（使文件被git管理）

```shell
# path支持正则
git add <path>
```

![image-20221027135635218](D:\0voice\git\git仓库和服务器搭建.assets\image-20221027135635218.png)

把文件从暂存区里移除

```shell
# 不是从磁盘上移除，只是不被git管理
git rm --cached
```

![image-20221027135551641](D:\0voice\git\git仓库和服务器搭建.assets\image-20221027135551641.png)

##### 提交到仓库，真正被git跟踪记录

```shell
git commit

# 例子1
# -a: 将'暂存区'和'当前已被跟踪的文件的所有修改'提交到仓库
# -m: 指定这次提交的message内容
git commit -a -m "xxx"

# 例子2
# 提交Makefile和Logger.cpp的修改
git commit Makefile Logger.cpp -m "修改编译错误，添加了对log4cpp库的依赖"
```

用法如下：

![image-20221027141243735](D:\0voice\git\git仓库和服务器搭建.assets\image-20221027141243735.png)

##### 工作区、暂存区和仓库

![image-20221027141935648](D:\0voice\git\git仓库和服务器搭建.assets\image-20221027141935648.png)

---

#### git服务器  ——  创建一个git的中央服务器

##### 创建git账号和git用户组

```shell
sudo adduser git  			# 添加git用户
sudo passwd git   			# 添加git的密码
sudo groupadd git 			# 添加git用户组
sudo usermod -G git git		# 添加git用户到git用户组
```

##### 创建git仓库

注：`/srv` 目录主要用来存放一些系统提供的网络服务的数据

```shell
cd /srv 
mkdir nginx-docs.git
cd nginx-docs.git
git init --bare  # bare选项指定该仓库为裸仓库
sudo chown -R git:git /srv/nginx-docs.git # 修改权限为git用户
```

##### 禁止git用户登录shell，这样git通过sh服务登录会被拒绝

`chsh git`

##### 克隆远端仓库

```shell
git clone git@ip:/srv/nginx-docs.git
```

这个过程中要输入用户名和密码

可以通过RSA认证的方式省略掉密码的输入

##### 免密输入的配置

通过RSA认证，生成`公钥`和`私钥`，然后把客户端的公钥告诉git服务器

```shell
=== 在客户端机器上
ssh-keygen -t rsa    # 在显示的文件下生成 rsa密钥对
# id_rsa.pub 公钥文件,  id_rsa 私钥文件

=== 在git服务器上
su git
ssh-keygen -t rsa
touch authorized_keys
将客户端的id_rsa.pub 追加到authorized_keys文件中
```

