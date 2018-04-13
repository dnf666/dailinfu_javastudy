### docker ps 

    查看所有运行镜像


## docker logs 镜像名 

    查看输出

###  docker run 镜像名 执行命令 
    如果加上 -d 如 docker run -d 镜像名 执行命令  表示后台运行

## docker stop 镜像名或者id
    停止容器
### docker search 镜像名
    查询可下载镜像
    
### docker pull 镜像名
    下载镜像
    
### docker rm 容器
    删除容器

#### docker pause 
    暂停容器中所有的进程。
#### docker unpause 
    恢复容器中所有的进程。
    
### docker cp 
    用于容器与主机之间的数据拷贝
    将主机/www/runoob目录拷贝到容器96f7f14e99ab中，目录重命名为www。
    docker cp /www/runoob 96f7f14e99ab:/www