# n6dlb
矩尺分布式应用交付平台

## 介绍
本系统由管理节点与转发引擎组成，先安装管理节点，然后添加转发引擎。(管理节点用于配置转发规则等, 转发引擎实现转发流量等)

## 环境
* 操作系统：Linux（如CentOS/Ubuntu/统信/Openeuler/Kylin/[redhat](https://catalog.redhat.com/software/applications/detail/269117)等）
* CPU 指令架构：x86_64, arm64
* 最低资源：2 核 CPU / 8 GB 内存 / 10 GB 磁盘
* 请确保这些[端口](https://docs.n6delta.com/v3.4.6/manual/operation-manual/soft-lb-install/environment.md##端口)未被占用，否则安装会失败。

可以根据以下命令来查看相关信息
``` bash
uname -m                                    # 查看指令架构
cat /proc/cpuinfo| grep "processor"         # 查看 CPU 信息
free -h                                     # 查看内存信息
df -h                                       # 查看磁盘信息
```

## 安装部署

请通过bash命令行安装管理节点，而安装完管理节点后，可以通过Web控制台安装转发引擎。

命令行安装管理节点时，如果目标主机可以连接互联网，可以通过[在线安装](#在线安装)采用联网方式从Docker仓库中拉取镜像。如果不能连接外网，则需要下载完整压缩包通过[离线安装](#离线安装)安装。

<!-- <span style="color: #FFD700;"> </span>-->
⚠️ 安装过程中请仔细选择选项, 以免覆盖已有配置(如docker)。

### 在线安装
```bash
bash -c "$(curl -fsSLk https://docs.n6delta.com/install_script/manage.sh)"
```
![安装成功](https://docs.n6delta.com/v3.4.6/assets/online-install-succ.CA48ZwCW.png)
<!-- sudo bash -c "$(curl -fsSLk https://www.normaedelta.com.cn/n6_install_v344.sh)" -->
### 离线安装
注: 依赖 NetworkManage 1.41.3 版本以上([详情](https://docs.n6delta.com/v3.4.6/manual/operation-manual/soft-lb-install/environment.md#操作系统及NetworkManage版本要求))
1. 下载安装包至服务器
    - 浏览器下载

        x86架构[n6_x64_3.4.6.tar.gz](https://github.com/normaedelta/n6dlb/releases/download/3.4.6/n6_x64_3.4.6.tar.gz.xz)

        arm64架构[n6_arm_3.4.6.tar.gz](https://github.com/normaedelta/n6dlb/releases/download/3.4.6/n6_x64_3.4.6.tar.gz.xz)
2. 解压并安装
```bash
sudo xz -d n6_x64_3.4.6.tar.gz.xz 
sudo tar -zxf n6_x64_3.4.6.tar.gz && sudo bash n6_install.sh
```
![安装成功](https://docs.n6delta.com/v3.4.6/assets/offline-install-succ.C59RKZA1.png)

## 管理节点控制台
安装成功以后，你可以打开浏览器访问 https://[manage-ip]/ 进行配置。manage-ip是安装时指定的管理IP。
![登录页面](https://docs.n6delta.com/v3.4.6/assets/login.BNxD5zVY.png)

[HTTP虚拟服务转发流量](https://docs.n6delta.com/v3.4.6/config/quick-guide/l7-vs-config.html)

[完整功能见用户手册](https://docs.n6delta.com/v3.4.6/manual/operation-manual/slb/virtual-service.html)
