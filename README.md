![logo-blue](https://user-images.githubusercontent.com/51039935/197520391-f35db354-6071-4c12-86ea-fc450f04bc85.png)
# NAS媒体库管理工具

[![GitHub stars](https://img.shields.io/github/stars/hsuyelin/nas-tools?style=plastic)](https://github.com/hsuyelin/nas-tools/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/hsuyelin/nas-tools?style=plastic)](https://github.com/hsuyelin/nas-tools/network/members)
[![GitHub issues](https://img.shields.io/github/issues/hsuyelin/nas-tools?style=plastic)](https://github.com/hsuyelin/nas-tools/issues)
[![GitHub license](https://img.shields.io/github/license/hsuyelin/nas-tools?style=plastic)](https://github.com/hsuyelin/nas-tools/blob/master/LICENSE.md)
[![Docker pulls](https://img.shields.io/docker/pulls/hsuyelin/nas-tools?style=plastic)](https://hub.docker.com/r/hsuyelin/nas-tools)
[![Platform](https://img.shields.io/badge/platform-amd64/arm64-pink?style=plastic)](https://hub.docker.com/r/hsuyelin/nas-tools)

TG频道：https://t.me/nastool_official (官方)

Wiki：https://t.me/NAStool_wiki

API: http://localhost:3000/api/v1/

## 功能：

NAS媒体库管理工具。

## 安装
### 1、Docker
```
docker pull hsuyelin/nas-tools:latest
```
教程见 [这里](https://raw.githubusercontent.com/hsuyelin/nas-tools/master/docker/readme.md) 。

如无法连接Github，注意不要开启自动更新开关(NASTOOL_AUTO_UPDATE=false)，将NASTOOL_CN_UPDATE设置为true可使用国内源加速安装依赖。

### 2、本地运行
仅支持python3.10版本，需要预安装cython（python3 -m pip install Cython），如发现缺少依赖包需额外安装：
```
git clone -b master https://github.com/hsuyelin/nas-tools --recurse-submodule 
python3 -m pip install -r requirements.txt
export NASTOOL_CONFIG="/xxx/config/config.yaml"
nohup python3 run.py & 
```

### 3、可执行文件运行
仅支持python3.10版本，先从tag下载对应的可执行文件，打开终端，例如下载的是macos版本，文件名为：nastool_macos_v3.2.2：
```
mv nastool_macos_v3.2.2 nastools
chmod +x nastools
./nastools（如果需要不在终端输出执行：./nastool &> /dev/null）
```

### 4、关于 Cloudflare IP优选插件
• 必须开启自定义Hosts插件
• 优选ip：自定义hosts中需要定时更新的域名ip
• 优选周期：5位cron表达式（分 时 天 月 周）
• 自动校准：开启后会获取自定义Hosts插件中，出现频率最高的ip作为优选ip
• 高级参数：-dd -t 1
可大大减少优选时间（-dd:禁用测速；-t 1失败一次后放弃）

注意问题：
• 打开站点，F12看请求的response的Server属性，如果是cloudflare，则可添加到自定义Hosts插件
• cf优选插件当前版本显示暂未安装
1. 基础设置—日志等级调整为debug，docker logs -f nt容器名看插件执行日志排查问题
2.如果没有设置代理服务器添加代理服务器试试， 如果设置已代理服务器，把代理服务器删掉试试（本地或者梯子网络访问github api受限）
3.手动下载[最新版本CloudflareSpeedTest](https://github.com/XIU2/CloudflareSpeedTest/releases)，压缩包直接放于nt容器/config/plugins/CloudflareSpeedTest/路径下，再次插件立即运行一次即可


## 免责声明
1) 本软件仅供学习交流使用，软件本身不提供任何内容，仅作为辅助工具简化用户手工操作，对用户的行为及内容毫不知情，使用本软件产生的任何责任需由使用者本人承担。
2) 本软件代码开源，基于开源代码进行修改，人为去除相关限制导致软件被分发、传播并造成责任事件的，需由代码修改发布者承担全部责任。同时按AGPL-3.0开源协议要求，基于此软件代码的所有修改必须开源。
3) 本项目没有在任何地方发布捐赠信息页面，也不会接受任何捐赠，请仔细辨别避免误导。
