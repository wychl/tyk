## docker启动

-  修改host文件

We are assuming that you are running this on a local Docker installation, the Tyk Portal requires a domain name to bind to in order to work properly, so let’s make sure we set that up in /etc/hosts:

    127.0.0.1    www.tyk-portal-test.com
    

- 获取compose文件
 
 ```bash
  git clone https://github.com/lonelycode/tyk_quickstart.git
  cd tyk_quickstart
 ```

-  在tyk_analytics.conf文件中加入license_key


    {
        ...
        "mongo_url": "mongodb://mongo:27017/tyk_analytics",
        "license_key": "LICENSEKEY",
        "page_size": 10,
        ...
    }
    

-  启动

```bash
 docker-compose up -d --force-recreate
    ./setup.sh
```

-  登录
 
    127.0.0.1:3000