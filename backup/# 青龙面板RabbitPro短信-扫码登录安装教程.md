
# 青龙面板RabbitPro短信/扫码登录安装教程

### FAKER整理 TG频道 https://t.me/Soucetalk

### 2024-03 RabbitPro暂时无法获取新许可，已有许可需要重装最新版本的可继续操作。

### 注意：本教程基于Cent OS7.6系统，Faker一键安装版Docker青龙配置，如有不同配置自行注意。

[【新手推荐】青龙稳定版一键配置（QL pannel Faker Repository environment Setup）](https://www.notion.so/QL-pannel-Faker-Repository-environment-Setup-45edcbfe90d74d8abb2d71896eab3be7?pvs=21) 

### 第一步 配置Docker

由于RabbitPro打包较大，我们先配置一下Docker国内源，加速下载。

[配置免费阿里云docker加速](https://www.notion.so/docker-7251011a983a44fca44b3b58eaa2d9d1?pvs=21)

### 第二步 安装配置Rabbit Pro

**Rabbit群已暂停开放，暂时无法获取Token，新用户请耐心等待，已有Token可继续操作。**

先到Rabbit群，获取Token。

https://t.me/RabbitOneA

进群后在群里发送指令然后找机器人。剩余积分这些不用管，目前是免费的。保存好你的Token。

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/ab86454e-d8fc-47db-8b72-d95ac7149dba/5d470444-3791-4837-a5d6-5c43a209e557/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/ab86454e-d8fc-47db-8b72-d95ac7149dba/79d4d68c-e677-46c8-aba3-c4e093b58b02/Untitled.png)

在FinalShell命令框一行一行输入

```bash
mkdir /root/Rabbit
cd /root/Rabbit
```

然后在命令行窗口输入

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/ab86454e-d8fc-47db-8b72-d95ac7149dba/c64a256f-4b8a-4dc0-a081-23560f223b10/Untitled.png)

```bash
docker run   --name rabbitpro --restart=always -p 5702:1234  -d  -v  "$(pwd)"/data:/Rabbit/data \
-it --privileged=true  shufflewzc/qrbbitpro:latest
```

等待安装，安装完成后到浏览器打开 ip:5702/admin 账号和密码都是admin。（ip是你的云服务器ip）

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/ab86454e-d8fc-47db-8b72-d95ac7149dba/5d6e01e8-f9f7-4ea1-887d-9eaafc2092ee/Untitled.png)

按照页面要求，把Token写上，其他的随便写，登录人数和回收时间按我的就行。

ServerHost我们随便选一个。

```bash
可用host：
jd-orgin.1888866.xyz
[mr.yanyuwangluo.cn:1202](http://mr.yanyuwangluo.cn:1202/) (烟雨)
mr.118918.xyz
[mr.5gyh.com](http://mr.5gyh.com/)
host.257999.xyz
[log.madrabbit.eu.org](http://log.madrabbit.eu.org/) (cf反代)
fd.gp.mba:6379 (Wavefork)
mr.108168.xyz:10188 (Tam)
rabbit.gushao.club (孤傲)
```

填写完保存就行。

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/ab86454e-d8fc-47db-8b72-d95ac7149dba/9d032fe6-1f63-45f8-9155-3edeca6696c5/Untitled.png)

然后到容器管理页面，添加容器。容器容量记得调多点。

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/ab86454e-d8fc-47db-8b72-d95ac7149dba/9b80cfec-b4fa-4b15-bd24-e9831e994efe/Untitled.png)

应用ID和秘钥，到青龙里面创建一个，权限全选就行。填写完后测试链接，链接成功就可以了。

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/ab86454e-d8fc-47db-8b72-d95ac7149dba/b6fc5947-d7da-420d-9b86-e353d7e38af4/Untitled.png)

然后就配置完成了。访问地址是 ip:5702

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/ab86454e-d8fc-47db-8b72-d95ac7149dba/24c751e0-b733-4f2f-b35d-58ab26504f8d/Untitled.png)

教程到这里就结束了，由于RabbitPro是Beta版本，可能会有一些Bug，遇到Bug重启就行了。有问题可以到群里反馈。

## 2024-01 更新 升级命令和通知教程

```bash
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower -c --run-once rabbitpro
```

### WxPusher配置教程

### 1. 配置登录提醒，管理页面登录提醒等

- 进入配置文件界面：`http://ip:5702/admin#/settings/settings`
- 添加WXPUSHER_APP_TOKEN和WXPUSHER_UID
- 点击测试发送通知，收到通知即配置成功

> wxpusher教程，进入管理页面，新建一个应用，保存好appToken，然后点击关注应用，打开微信扫描二维码，关注后，点击 我的 -> 我的UID ，即可获取uid
> 

### 2. 配置一对一通知

- 进入容器管理页，新建容器或者编辑容器，滑至最下方，将前面获取的appToken填入WxPusher框内，点击保存
- 进入wxpusher的[管理页面](https://wxpusher.zjiecode.com/admin/main/app/appInfo)，选择刚刚创建的应用，点击修改，在事件回调地址处填写你的服务器地址，例如：http://ip:5702/api/wxpusher ，ip需要公网可访问的，不确定ipv6是否可行
- 扫码或短信登录完后，点击当前账号位置切换至需要绑定通知的账号，打开微信扫描下方的二维码，收到绑定成功的通知即为绑定成功
- 过期通知模板可在管理页面的过期通知处进行修改，注意修改时，{{ pin }}不要删掉，位置任意

### 2024-3-15 已有镜像修复教程

老样子打开FInalShell

```bash
docker stop rabbitpro
docker rm rabbitpro
cd 
```

[https://thin-hill-428.notion.site/docker-7251011a983a44fca44b3b58eaa2d9d1?pvs=4](https://www.notion.so/docker-7251011a983a44fca44b3b58eaa2d9d1?pvs=21)