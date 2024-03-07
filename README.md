docker run -dit \
-v /root/ql/config:/ql/config \
-v /root/ql/log:/ql/log \
-v /root/ql/db:/ql/db \
-v /root/ql/scripts:/ql/scripts \
-v /root/ql/jbot:/ql/jbot \
-v /root/ql/repo:/ql/repo \
-p 5710:5700 \
-e ENABLE_HANGUP=true \
-e ENABLE_WEB_PANEL=true \
--name ql \
--hostname ql \
--privileged=true \
--restart always \
whyour/qinglong:2.16.5

hppro  docker版
docker run --restart=always -P -d -e deviceId=6b3ef30a52234ee2940341ff809ee4ae registry.cn-shenzhen.aliyuncs.com/hserver/hp-pro:latest


chmod -R 777 ./hp-client

./hp-client -deviceId=6b3ef30a52234ee2940341ff809ee4ae

#如果你想让他在后台运行，可以使用nohup命令

nohup ./hp-client -deviceId=6b3ef30a52234ee2940341ff809ee4ae

Linux一键部署
bash <(curl -sSL https://www.hpproxy.cn/hp-doc/hppro.sh)

6b3ef30a52234ee2940341ff809ee4ae
