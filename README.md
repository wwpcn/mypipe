# 容器云部署Xray高性能代理服务

在容器云部署Xray高性能代理服务，通过ws传输的(vmess、vless、trojan、shadowsocks、socks)等协议

Kxxxb：待发布

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

6. 打开容器云主页，按照提示创建一个应用

## 注意

请勿滥用本仓库

## 赞助我们

爱发电：https://afdian.net/a/misaka-blog

## 频道及交流群

[Telegram 频道](https://t.me/misakablogchannel)

[Telegram 群组](https://t.me/+CLhpemKhaC8wZGIx)

## License
GNU Affero General Public License v3.0
