# docker-compose 启动tyk

**运行环境**
- docker
- docker-compose

## 第一步:

在 hosts文件中加入以下配置

```
127.0.0.1 www.tyk-portal-test.com
127.0.0.1 www.tyk-test.com
```

## 第二步: 添加dashboard的license

 将[tyk_analytics.conf](confs/tyk_analytics.conf)文件中的`"license_key": ""` 设置为自己[获取license](https://tyk.io/shop/checkout/)值

## 第三步：运行[docker-compose](docker-compose.yml)文件:

```bash
docker-compose up -d
```

# 第四步: 运行 [set.sh](setup.sh) 脚本

```bash
chmod +x setup.sh 
./setup.sh 
```

这个脚本会生成一对用户名和密码，和dashboard的url

## 第五步: 登录dashboard

http://www.tyk-test.com:3000

