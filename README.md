# 使用 Docker 快速搭建 lanmp 环境

运行环境集成了apache + nginx + mysql + php

### 第一步，准备环境
- window 推荐用win10操作系统， 并且有hyper-v虚拟机的功能, 添加hyper-v的路径，控制面板\程序
- Git
- Docker   centos安装参考链接： https://91helpme.com/docker-2crp1
- Docker-compose  centos参考链接： https://91helpme.com/docker-xeuoz


### 第二步，获取项目代码

```
git clone https://github.com/luohuacc/docker-lanmp
```

### 第三步，启动运行

```
cd docker-lanmp
docker-compose up -d   //创建容器
```


### 第四步，启动运行

默认已经配置好相关demo文件

测试apache：

- http://localhost 
- https://localhost

测试nginx：
- http://localhost:8080
- https://localhost:4343

如果访问出现以下内容，说明环境搭建成功
```markdown
this is apache+php test
this is nginx+php test

```


## 容器相关命令管理

1. 查看运行的容器

```
docker-compose ps   //如果state的状态为up 说明容器启动成功
```
2. 启动、重启、停止 服务

```
docker-compose  start  //启动所有服务
docker-compose  stop   //停止所有服务
docker-compose restart //重启所有服务
```
3. 查看服务的日志

```
docker-compose logs  //查看所有服务的日志
docker-compose logs nginx  //查看nginx的服务日志
docker-compose logs apache //查看apache
docker-compose logs mysql  //查看mysql
```

4. 进入到某个服务

```
docker-compose exec apache bash   //进入apache服务的命令
```
5. 使用php的composer和php命令

```
docker-compose exec php72 composer  //使用php72服务的composer命令
docker-compose exec php72 php -v   //使用php72服务的php命令行工具
```

## 目录结构

conf   配置文件的目录，包括
conf/apache/extra/httpd-vhosts.conf 配置虚拟主机的文件
conf/apache/extra/httpd-ssl.conf 配置https的主机的文件
conf/nginx/conf.d/demo.conf 配置nginx的主机的文件， 也可以新加文件，但是后缀以.conf结尾

www    网站的根目录
docker-compose.yml  容器的编排工具

以上这些是默认有的目录， 如果运行成功的话，还会出现以下目录 

log  日志目录 
mysql mysql的数据存放目录 
portainer docker的gui管理工具  （localhost:9000）


