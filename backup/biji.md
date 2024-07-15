bash <(curl -s -L https://git.io/v2ray-setup.sh)

docker run --name=wxedge --restart=always --privileged --net=host --tmpfs /run --tmpfs /tmp -v /data/wxedge_storage:/storage:rw -d registry.cn-hangzhou.aliyuncs.com/onething/wxedge
     ip：18888

1Panel 是新一代的 Linux 服务器运维管理面板
RedHat / CentOS

curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && sh quick_start.sh

Ubuntu

curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && sudo bash quick_start.sh

Debian

curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && sh quick_start.sh