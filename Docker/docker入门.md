# Docker入门

> 通过 Docker 化 JPress 应用，熟悉 Docker 的基本命令。

## 下载

下载 Docker for Windows： <https://hub.docker.com/ 【 Docker 镜像仓库的默认下载地址，我使用的国内镜像市场： <https://hub.daocloud.io/> 】

## 基础命令

- docker --help：获取 docker 帮助信息

- docker COMMAND --help：获取 docker 子命令的帮助信息

- docker pull [OPTIONS] NAME[:TAG|@DIGEST]：拉取镜像到本地，TAG 默认是 latest，NAME 可指定仓库地址，比如：daocloud.io/library/nginx

- docker images [OPTIONS] [REPOSITORY[:TAG]]：列出所有镜像，OPTIONS 默认是 -a|-all，指定 [REPOSITORY[:TAG]] ，便是查询是否存在该本地镜像

- docker run [OPTIONS] IMAGE [COMMAND] [ARG...]：在一个新的容器中执行命令，默认是在前台执行

- - docker run -d ：后台执行，返回CONTAINER-ID，比如：tomcat、mysql 等持久运行的容器，前台执行时会挂起
  - -p、-P：开放一个指定端口映射到主机上、随机映射所有端口

- docker stop [OPTIONS] CONTAINER [CONTAINER...]：停止一或多个容器

- docker ps [OPTIONS]：列出所有容器

- docker exec [OPTIONS] CONTAINER COMMAND [ARG...]：在一个运行中的容器中，执行一个命令

- - 常用：docker exec -it CONTAINER-ID bash 【Windows下，加上前缀 winpty docker ... 】

- docker build [OPTIONS] PATH | URL | -：Build an image from a Dockerfile，创建镜像



## 图解

![1560592283369](C:\Users\Joian\AppData\Roaming\Typora\typora-user-images\1560592283369.png)



## 自定义 JPress 镜像



1、自制定一个JPress 镜像：Dockerfile 和 必须的 war 包单独放在一个文件夹中，可加快构建速度

- Dockerfile

  ```dockerfile
  from daocloud.io/library/tomcat
  label maintainer="Joians <joiansun@qq.com>"
  copy jpress.war /usr/local/tomcat/webapps
  ```

- JPress： <https://gitee.com/fuhai/jpress/blob/alpha/wars/> 下载 war 包，【jpress.io 提供的内容过新，没有 war 包】
- 执行：docker build -t jpress:latest .

2、将自制定的镜像运行在 Docker 容器中

```dockerfile
docker run -d -p 9999:8080 jpress
netstat -na|grep 9999：查看端口状态
curl localhost:9999：查看指定地址内容
```

3、下载并在单独的容器中运行 mysql：解决无法成功配置 JPresss 数据库的问题：使用 mysql5.6 代替 latest 版本的 mysql【mysql 新版本和 JPress 无法很好的融合】

```dockerfile
docker pull mysql:5.6
docker run -d -p 3306:3306 --name mysql5.6 -e MYSQL_DATABASE="jpress" -e MYSQL_ROOT_PASSWORD="1234" mysql:5.6
# 未执行这个
docker run -d -p 9999:8080 --link mysql5.6:mysql jpress
```

4、JPress 配置 mysql 时，因 mysql 和 jpress 不在一个容器内（Docker 隔离性），需获取执行 mysql 进程的容器地址，用以配置 JPress ：

```dockerfile
# windows 执行时，需加 winpty 前缀
winpty docker exec -it mysql-CONTAINER-ID bash
# cat /etc/hosts：查看 mysql 所在容器的 ip
# 使用 mysql 所在容器的 ID 搜索 ip
```

5、JPress 配置完成之后，需要重启 jpress 容器：`docker restart [docker-ID]` ，不可先 stop 在进行 start

- 猜测可能是 容器环境未保存。**表现**为：再次启动之后，需要重新配置 JPress 数据库，并且 CONTAINER-ID 不同

## 总结 

![1560593004170](C:\Users\Joian\AppData\Roaming\Typora\typora-user-images\1560593004170.png)

