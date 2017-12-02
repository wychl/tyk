## 获取用户列表
属性|描述
---|---
url|`api/users`
请求方法|GET
authorization| 用户的访问凭证


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X GET \
     http://127.0.0.1:3000/api/users | python -mjson.tool
```

**返回样本示例**
```json
{
    "pages": 0,
    "users": [
        {
            "access_key": "859cdd67aacb42c0750162ce6ac39ab3",
            "active": true,
            "api_model": {},
            "email_address": "test7917@test.com",
            "first_name": "John",
            "id": "59eee1198f3cf5a56213d740",
            "last_name": "Smith",
            "org_id": "59eee119d404630001831723",
            "user_permissions": {
                "analytics": "read",
                "apis": "write",
                "hooks": "write",
                "idm": "write",
                "keys": "write",
                "oauth": "write",
                "policy": "write",
                "portal": "write",
                "system": "write",
                "users": "write"
            }
        },
        {
            "access_key": "",
            "active": false,
            "api_model": {},
            "email_address": "test@jasonsonson.com",
            "first_name": "test",
            "id": "59f6c6656ffb3ca780179761",
            "last_name": "test",
            "org_id": "59eee119d404630001831723",
            "user_permissions": {}
        }
    ]
}

```

## 检索特定用户
属性|描述
---|---
url|`/api/users/{user-id}`
请求方法|GET
authorization| 用户的访问凭证


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X GET \
     http://127.0.0.1:3000/api/users/59eee1198f3cf5a56213d740 | python -mjson.tool
```

**返回样本示例**
```json
{
    "access_key": "859cdd67aacb42c0750162ce6ac39ab3",
    "active": true,
    "api_model": {},
    "email_address": "test7917@test.com",
    "first_name": "John",
    "id": "59eee1198f3cf5a56213d740",
    "last_name": "Smith",
    "org_id": "59eee119d404630001831723",
    "user_permissions": {
        "analytics": "read",
        "apis": "write",
        "hooks": "write",
        "idm": "write",
        "keys": "write",
        "oauth": "write",
        "policy": "write",
        "portal": "write",
        "system": "write",
        "users": "write"
    }
}
```
