#### github介绍

github利用git进行版本控制、专门用于存放软件代码和内容的共享虚拟主机服务。

github平台的一些词条

> repo：项目，绝大多数的开源项目都会放在github上。基于repo可以提issue，可以review code，可以有wiki，branch，tag等等，还可以star和fork这样的repo
>
> Explore：基于兴趣显示的一些开源项目
>
> Topics：按照主题显示的一些项目
>
> Trending：流行repo，可以选择语言和周期来显示
>
> Events：显示github官方的活动



##### 建立自己的repo

一、注册github账号

二、添加ssh key

```shell
git config --global user.name xxx
git config --global user.email xxx
ssh-keygen -t rsa
```

在设置里添加

![image-20221029183152433](D:\0voice\git\github使用.assets\image-20221029183152433.png)

三、创建repo

右上角的new repository

```shell
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/Bercoke/Git-.git
git push -u origin main
```

##### 下载开源的项目

```shell
# url：https://github.com/torvalds/linux
git clone https://github.com/torvalds/linux.git
```

