## [安装之前现卸载系统上原有的Docker]
`yum remove docker \`
>                   docker-client \
>                   docker-client-latest \
>                   docker-common \
>                   docker-latest \
>                   docker-latest-logrotate \
>                   docker-logrotate \
>                   docker-engine`

## 2、安装需要的安装包yum-utils
`yum install -y yum-utils`
## 3、设置镜像仓库地址
`yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo` 
  ##此地址为官方的仓库地址，在国内建议不要用
 `yum-config-manager \
  --add-repo \
   http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo` 
 #阿里云的镜像仓库地址
## 4、安装docker相关的引擎
#先更新yum软件包索引
 	`yum makecache fase` 
## 默认安装最新的docker
`yum install docker-ce docker-ce-cli containerd.io`
## 5、启动docker
`systemctl start docker`
`systemctl enable docker`
验证安装是否成功
`docker version`

## 重启容器
`docker restart r`


`docker ps -a`

`docker rm `                <CONTAINER_ID or CONTAINER_NAME>
`docker rm -f `              <CONTAINER_ID or CONTAINER_NAME>

`docker images`
`docker rmi `        <镜像ID>
`docker rmi -f `    <镜像ID>