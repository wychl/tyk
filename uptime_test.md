## uptime

检测服务是否可以正常运行

### tyk.conf
```json
{
    "uptime_tests": {
        "disable": false, // false时 运行uptime tests 
        "config": {
            "enable_uptime_analytics": true,
            "failure_trigger_sample_size": 3,
            "time_wait": 300,//运行时间间隔
            "checker_pool_size": 50 //实例
        }
    }
}
```


### api配置

```json
{
  uptime_tests: {
      check_list: [
          {
              "url": "http://google.com/"//服务的url
          },
          {
              "url": "http://posttestserver.com/post.php?dir=uptime-checker",
              "method": "POST",
              "headers": {
                  "this": "that",
                  "more": "beans"
              },
              "body": "VEhJUyBJUyBBIEJPRFkgT0JKRUNUIFRFWFQNCg0KTW9yZSBzdHVmZiBoZXJl"
          }
      ]
  }
}

```

## 事件
- uptime 事件 添加uptime webhook
- downtime事件 添加 downtime webhook