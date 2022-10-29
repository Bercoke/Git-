#### Git的安装与配置

##### 安装git

```shell
# unbuntu 为例
sudo apt-get install git
```

##### 配置git

配置用户名和邮件地址：每一次git提交都会使用这些信息

```shell
# --global是系统全局设置，特定项目只在特定目录下设置
git config --global user.name "xxx"
git config --global user.email 
# 查看配置信息
git config --list
```

获取帮助

```shell
git help <verb>
git <verb> --help
man git-<verb>
# 例如：git help config
```

**git官方文档**：https://git-scm.com/book/zh/v2
