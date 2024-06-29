## 1.开源项目选定
现在gpt很火,git中大佬们都创建了很多高星项目,我这里选用了chatgpt-on-wechat(项目地址:https://github.com/zhayujie/chatgpt-on-wechat),这个项目在扩展时也很舒服,大家可以去拉下来看看,学习源码才能方便后续的扩展
## 2.服务器选定
国内服务:前置条件需要走代理(这个不方便说,项目中也有对应的方案,大家可以看一下)
国外服务器:没有前置条件
配置方面自己玩的1核1G也可以正常运行
## 3.ChatGPT ApiKey的获取
自己开发的话可以使用免费账号的apikey,在登陆账号后,访问以下地址
(1)新建apikey的地址:https://platform.openai.com/account/api-keys

(2)查看该账号额度的地址:https://platform.openai.com/account/usage

需注意不是所有的账号有key就可以用哈,大家要看看有没有额度,Expired 后面的时间是你额度的能使用的截止时间,超过这个时间,就是有额度也用不了了
## 4.部署项目\ndocker方式：
(1)拉取python镜像,进入容器
sudo docker pull python:3.9
sudo docker run -it --name wechatbot python:3.9 bash
(2)克隆项目代码
git clone https://github.com/zhayujie/chatgpt-on-wechat chatgpt-on-wechat-ai\ncd chatgpt-on-wechat-ai/
普通部署方式：
(1)配置python3.8或3.9环境,网上好多教程,此处不做赘述
(2)克隆项目代码,拷贝时请按自己的路径进行修改
cd /home/admin/wechatbot
git clone https://github.com/zhayujie/chatgpt-on-wechat chatgpt-on-wechat-ai
cd chatgpt-on-wechat-ai/
项目配置：
(1)安装相关依赖
#安装核心依赖 (必选)
#能够使用'itchat'创建机器人，并具有文字交流功能所需的最小依赖集合。
pip3 install -r requirements.txt
#拓展依赖 (可选，建议安装)
pip3 install -r requirements-optional.txt
#如果某项依赖安装失败请注释掉对应的行再继续。
#其中'tiktoken'要求'python'版本在3.8以上，它用于精确计算会话使用的tokens数量，强烈建议安装。
(2)修改配置文件
cp config-template.json config.json
#然后在'config.json'中填入配置，以下是对默认配置的说明，可根据需要进行自定义修改（请去掉注释）:
#config.json文件内容示例
{  "open_ai_api_key": "YOUR API KEY",                  #填入上面创建的 OpenAI API KEY
  "model": "gpt-3.5-turbo",                      #模型名称 还可以填写text-davinci-003
  "proxy": "",                                          #代理客户端的ip和端口 外网填空
 "single_chat_prefix": ["bot", "@bot"],      #私聊时文本需要包含该前缀才能触发机器人回复
  "single_chat_reply_prefix": "[bot] ",             #私聊时自动回复的前缀，用于区分真人
  "group_chat_prefix\": ["@bot"],                    #群聊时包含该前缀则会触发机器人回复
  "group_name_white_list": ["ChatGPT测试群", "ChatGPT测试群2"],#开启自动回复的群名称列表
  "group_chat_in_one_session": ["ChatGPT测试群"],           #支持会话上下文共享的群名称  
  "image_create_prefix\": ["画", "看", "找"],                       #开启图片回复的前缀
  "conversation_max_tokens": 1000,                         #支持上下文记忆的最多字符数
  "speech_recognition": false,                                     #是否开启语音识别
  "group_speech_recognition": false,                            #是否开启群组语音识别
  "use_azure_chatgpt": false,                                        #是否使用Azure 
  "character_desc": "你是ChatGPT, 一个由OpenAI训练的大型语言模型, 你旨在回答并解决人们的任何问题，并且可以使用多种语言与人交流。",                                        #人格描述
  "subscribe_msg": "感谢您的关注！
这里是ChatGPT，可以自由对话。
支持语音对话。支持图片输出，画字开头的消息将按要求创作图片。\\n支持角色扮演和文字冒险等丰富插件。
输入{trigger_prefix}#help 查看详细指令。"
}
(3) 项目运行

touch nohup.out                                   # 首次运行需要新建日志文件  
nohup python3 app.py & tail -f nohup.out          # 在后台运行程序并通过日志输出二维码