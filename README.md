# 部署文档

## 环境部署

至少需要两台机器 ，推荐使用Ubuntu系统，安装LXD环境方便。安装好LXD之后配置LXD的Cluster（如果不配置，可以使用本项目的alone模式，在main.py中修改）。

选择其中一台为管理机，git clone 本项目。在所有节点需要创建一个新用户（用于远程管理），此处以cloud用户为例。

### 管理机

管理机上执行：

```bash
adduser --disabled-password cloud
su - cloud
ssh-keygen -t rsa
```

记住管理机的公钥：`cat /home/cloud/.ssh/id_rsa.pub`

### 所有节点

在其它机器上执行：

```bash
adduser --disabled-password cloud
su - cloud
mkdir ~/.ssh
touch ~/.ssh/authorized_keys
chmod -R 600 ~/.ssh
```

修改`~/.ssh/authorized_keys`的内容为管理机的`id_rsa.pub`文件内容。

## 测试

确保管理机的`cloud`用户能免密码ssh到所有节点（包括管理机自身）。

## 配置

修改`main.py`，根据变量提示按需修改。

## 运行

`python3 main.py`

然后访问对应端口即可使用。