# webhooks
Webhook就是用户通过自定义回调函数的方式来改变Web应用的一种行为，这些回调函数可以由不是该Web应用官方的第三方用户或者开发人员来维护，修改。通过Webhook，你可以自定义一些行为通知到指定的URL去。

Webhook的“自定义回调函数”通常是由一些事件触发的，比如推送代码到代码库或者博客下新增一个评论，源站点会为Webhook进行HTTP请求的URI配置。

用户通过配置，就可以使一个网站上的事件调用在另一个网站上表现出来，这些事件调用可以是任何事件，但通常应用的是系统集成和消息通知。

## api 事件
- Quota Exceeded
- Rate limit exceeded
- Authentication Failure 授权失败
- Key Expired   token过期
- Version Access Failure
- Circuit Breaker Tripped
- Circuit Breaker Reset
- Uptime Test Host is Down
- Uptime Test Host is Up

## 获取hooks列表
属性|描述
---|---
url|`/api/hooks`
请求方法|GET
authorization| 用户的访问凭证


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X GET \
     http://127.0.0.1:3000/api/hooks | python -mjson.tool
```

**返回样本示例**
```json
{
    "hooks": [
        {
            "api_model": {},
            "event_timeout": 0,
            "header_map": {
                "x-test": "y-answer"
            },
            "id": "5a09143c7247dd0001fa5fad",
            "method": "GET",
            "name": "New Post Test",
            "org_id": "59eee119d404630001831723",
            "target_path": "http://192.168.2.80:9999/ping",
            "template_path": ""
        },
        {
            "api_model": {},
            "event_timeout": 0,
            "header_map": {
                "x-test": "y-answer"
            },
            "id": "5a0917517247dd0001fa5fae",
            "method": "GET",
            "name": "tes hooks",
            "org_id": "59eee119d404630001831723",
            "target_path": "http://192.168.2.80:9999/hooks",
            "template_path": ""
        },
        {
            "api_model": {},
            "event_timeout": 0,
            "header_map": {
                "x-test": "y-answer"
            },
            "id": "5a0919977247dd0001fa5faf",
            "method": "GET",
            "name": "tes hooks",
            "org_id": "59eee119d404630001831723",
            "target_path": "http://192.168.2.80:9999/hooks",
            "template_path": ""
        },
        {
            "api_model": {},
            "event_timeout": 0,
            "header_map": {
                "x-test": "y-answer"
            },
            "id": "5a0919987247dd0001fa5fb0",
            "method": "GET",
            "name": "tes hooks",
            "org_id": "59eee119d404630001831723",
            "target_path": "http://192.168.2.80:9999/hooks",
            "template_path": ""
        }
    ],
    "pages": 0
}

```

## 检索特定hook
属性|描述
---|---
url|`/api/hooks/{hook-id}`
请求方法|GET
authorization| 用户的访问凭证


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X GET \
     http://127.0.0.1:3000/api/hooks/59eee1198f3cf5a56213d740 | python -mjson.tool
```

**返回样本示例**
```json
 {
        "api_model": {},
        "id": "54be6c0beba6db07a6000002",
        "org_id": "54b53d3aeba6db5c35000002",
        "name": "Test Post",
        "method": "POST",
        "target_path": "http://httpbin.org/post",
        "template_path": "",
        "header_map": {
            "x-tyk-test": "123456"
        },
        "event_timeout": 0
    }
```
## 添加web hooks
属性|描述
---|---
url|`/api/hooks/`
请求方法|POST
authorization| 用户的访问凭证
target_path| 


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -s \
      -H "Content-Type: application/json" \
      -X POST \
      -d '{
                   "name": "tes hooks",
                   "method": "GET",
                   "target_path": "http://192.168.2.80:9999/hooks",
                   "header_map": {
                       "x-test": "y-answer"
                   }
          }' http://127.0.0.1:3000/api/hooks/ | python -mjson.tool
```

**响应样例**
```json
   {
       "Message": "Webhook created",
       "Meta": null,
       "Status": "OK"
   }
```

## 更新hook
属性|描述
---|---
url|`/api/hooks/{hook-id}`
请求方法|PUT
hook-id|hook的id
authorization| 用户的访问凭证


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -H "Content-Type: application/json" \
      -X PUT \
      - d '  {
                   "api_model": {},
                   "id": "54c2617aeba6db1edc000003",
                   "org_id": "54b53d3aeba6db5c35000002",
                   "name": "New Post Test",
                   "method": "PUT",
                   "target_path": "http://httpbin.org/post",
                   "template_path": "",
                   "header_map": {
                       "x-test": "y-answer"
                   },
                   "event_timeout": 0
               } ' http://127.0.0.1:3000/api/hooks/54c2617aeba6db1edc000003 | python -mjson.tool
```

**响应样例**
```json
     {
         "Status": "OK",
         "Message": "Webhook updated",
         "Meta": ""
     }
```


## 删除hook
属性|描述
---|---
url|`/api/hooks/{hook-id}`
请求方法|DELETE
hook-id|hook的id
authorization| 用户的访问凭证


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -H "Content-Type: application/json" \
      -X DELETE \
      http://127.0.0.1:3000/api/hooks/54c2617aeba6db1edc000003 | python -mjson.tool
```

**响应样例**
```json
    {
        "Status": "OK",
        "Message": "Webhook deleted",
        "Meta": ""
    }
```