# docker 使用说明
[TOC]

# 建立镜像：
  ## 准备工作
  - 用密钥登入ssh的，所以在生成自己的img之前要自己生成一个 vmkey.pub
    - 指令: ```ssh-keygen``` 生成的是一对公钥＆私钥，把公钥命名为 vmkey.pub 私钥命名为 vmkey
    - 当然，要把 vmkey.pub 放到 img.u2004 这个目录内，取代原来的 vmkey.pub
    - 用这个指令 ```echo `cat vmkey.pub` >> ~/.ssh/authorized_keys``` 然后后面启动后就可以免密码登入ssh了
  ## 编译image
  - 用以下指令建立 docker imgage, u2004 这个是 tag 名称，自己取一个适合的吧
    ```shell 
    docker build -f Dockerfile.df -t u2004 .
    ```

# 启动指令：
```docker run --name u2004 -p 22:22 -itd maleo/u2004:1.1```

# 有两个方式进去：
1. ssh 连入
  - 这跟启动指令有关，我启动容器时已经把 port 转出来了，所以就是本机 
```ssh root@localhost ```

2. docker 连入的指令
```docker exec -it u2004 /bin/bash ```