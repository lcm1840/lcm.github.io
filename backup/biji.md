docker run -d \

  --restart=always \

  --device=/dev/net/tun \

  --net=host \

  --cap-add=NET_ADMIN \

  --cap-add=SYS_ADMIN \

  --env PGY_USERNAME=19963258780 \

  --env PGY_PASSWORD=wagy \

  --name pgyvpn \

  benzbrake/pgyvpn

bash <(curl -s -L https://git.io/v2ray-setup.sh)

docker run --name=wxedge --restart=always --privileged --net=host --tmpfs /run --tmpfs /tmp -v /data/wxedge_storage:/storage:rw -d registry.cn-hangzhou.aliyuncs.com/onething/wxedge
     ip：18888

docker run -dit \
  -v $PWD/ql:/ql/data \
  -p 5700:5700 \
  --name ql-debian \
  --hostname ql-debian \
  --restart unless-stopped \
  whyour/qinglong:debian-python3.10

1Panel 是新一代的 Linux 服务器运维管理面板
RedHat / CentOS

curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && sh quick_start.sh

Ubuntu

curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && sudo bash quick_start.sh

Debian

curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && sh quick_start.sh