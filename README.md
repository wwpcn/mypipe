# 容器云部署Xray高性能代理服务

在容器云部署Xray高性能代理服务，通过ws传输的(vmess、vless、trojan、shadowsocks、socks)等协议

# 请勿使用常用的账号部署此项目，以免封号！！

关于本脚本加密sh文件的说明：由于部分容器云已识别本脚本，故不得不加密项目的sh文件代码

## 大致部署步骤

1. Fork本仓库并改名
    
2. 在`Dockerfile`内第3-5行修改自定义设置，说明如下：

`AUUID`：用来部署节点的UUID，如有需要可在[uuidgenerator](https://www.uuidgenerator.net/)生成

`CADDYIndexPage`：伪装站首页文件

`ParameterSSENCYPT`：ShadowSocks加密协议

3. 去[Docker Hub](https://hub.docker.com/)注册一个账号，如有账号可跳过
    
4. 编辑Actions文件`docker-image.yml`，按照“name: Docker Hub ID/自定义镜像名称”格式修改第13行
    
5. 添加Actions的Secrets变量，变量说明如下

`DOCKER_USERNAME`：Docker Hub ID

`DOCKER_PASSWORD`：Docker Hub 登录密码

6. 运行Actions任务，编译Dockerfile到Docker Hub中

7. 打开容器云主页，按照提示创建一个应用

## 节点配置

<details>
<summary>xray</summary>

```bash
* 客户端下载：https://github.com/XTLS/Xray-core/releases
* 代理协议：vless 或 vmess
* 地址：appname.herokuapp.com
* 端口：443
* 默认UUID：24b4b1e1-7a89-45f6-858c-242cf53b5bdb
* 加密：none
* 传输协议：ws
* 伪装类型：none
* 路径：/24b4b1e1-7a89-45f6-858c-242cf53b5bdb-vless // 默认vless使用/$uuid-vless，vmess使用/$uuid-vmess
* 底层传输安全：tls
```
</details>
  
<details>
<summary>trojan-go</summary>

```bash
* 客户端下载: https://github.com/p4gefau1t/trojan-go/releases
{
    "run_type": "client",
    "local_addr": "127.0.0.1",
    "local_port": 1080,
    "remote_addr": "appname.herokuapp.com",
    "remote_port": 443,
    "password": [
        "24b4b1e1-7a89-45f6-858c-242cf53b5bdb"
    ],
    "websocket": {
        "enabled": true,
        "path": "/24b4b1e1-7a89-45f6-858c-242cf53b5bdb-trojan",
        "host": "appname.herokuapp.com"
    }
}
```
</details>
  
<details>
<summary>shadowsocks</summary>

```bash
* 客户端下载：https://github.com/shadowsocks/shadowsocks-windows/releases/
* 服务器地址: appname.herokuapp.com
* 端口: 443
* 密码：password
* 加密：chacha20-ietf-poly1305
* 插件程序：xray-plugin_windows_amd64.exe  //需将插件https://github.com/shadowsocks/xray-plugin/releases下载解压后放至shadowsocks同目录
* 插件选项: tls;host=appname.herokuapp.com;path=/24b4b1e1-7a89-45f6-858c-242cf53b5bdb-ss
```
</details>

## 注意

请勿滥用本仓库

## 赞助我们

爱发电：https://afdian.net/a/misaka-blog

## 频道及交流群

[Telegram 频道](https://t.me/misakablogchannel)

[Telegram 群组](https://t.me/+CLhpemKhaC8wZGIx)

## License
GNU Affero General Public License v3.0
