## 查询定义的api列表
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X GET \
     http://127.0.0.1:3000/api/apis | python -mjson.tool
```

## 检索特定的api
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X GET \
     http://127.0.0.1:3000/api/apis/{id} | python -mjson.tool
```

## 创建api
```bash
curl -H "Authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
     -s \
     -H "Content-Type: application/json" \
     -X POST \
     -d '{
        "api_definition": {
            "name": "wytest",
            "slug": "test-wytest-api",
            "auth": {
                "auth_header_name": "Authorization"
            },
            "definition": {
                "location": "header",
                "key": "x-api-version"
            },
            "version_data": {
                "not_versioned": true,
                "versions": {
                    "Default": {
                        "name": "Default",
                        "use_extended_paths": true
                    }
                }
            },
            "proxy": {
                "listen_path": "/test-wytest-api/",
                "target_url": "http://httpbin.org/",
                "strip_listen_path": true
            },
            "active": true
        }
     }' http://localhost:3000/api/apis/ | python -mjson.tool
```
 
## 更新api
```bash
curl -H "Authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
     -s \
     -H "Content-Type: application/json" \
     -X PUT \
     -d '{
        "api_definition": {
            "name": "wytest",
            "slug": "test-wytest-api",
            "auth": {
                "auth_header_name": "Authorization"
            },
            "definition": {
                "location": "header",
                "key": "x-api-version"
            },
            "version_data": {
                "not_versioned": true,
                "versions": {
                    "Default": {
                        "name": "Default",
                        "use_extended_paths": true
                    }
                }
            },
            "proxy": {
                "listen_path": "/test-wytest-api/",
                "target_url": "http://httpbin.org/",
                "strip_listen_path": true
            },
            "active": true
        }
     }' http://localhost:3000/api/apis/{id} | python -mjson.tool
```

## 删除api
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X DELETE \
     http://127.0.0.1:3000/api/apis/{id}
```

## 测试api
-   api key

```bash
     curl -H "Authorization: 5a0bb9b973169000018c79314442f59f24cd4c416f1758185eab1931" http://127.0.0.1/test2/
```

```bash
     curl -H "Authorization: 5a0bb9b973169000018c7931abner" http://127.0.0.1:8080/test2/

```


```bash
     curl -H "Authorization: 5a1e7439d96b6200013e79cc1ab3f8e438d74697984198635429e261"  http://www.tyk-test.com:8181/string/?lower=hello

```


```bash
curl -X POST "http://www.tyk-test.com:8181/strings-outer/" -H "accept: application/json" -H "Authorization: 5a1e7439d96b6200013e79cccbb8b7db7e1942d78d31f177c479d0b0" -H "Content-Type: application/json" -d "{ \"action\": \"toUper\", \"input\": \"hello\"}"
```