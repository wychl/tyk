## 获取策略列表
属性|描述
---|---
url|`/api/portal/policies/`
请求方法|GET
authorization| 用户的访问凭证


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X GET \
     http://127.0.0.1:3000/api/portal/policies/ | python -mjson.tool
```

**响应样例**
```json
{
    "Data": [
        {
            "_id": "59ef023ed40463000183172e",
            "access_rights": {
                "241e6d340da448a95f4b36387249c738": {
                    "allowed_urls": [],
                    "apiid": "241e6d340da448a95f4b36387249c738",
                    "apiname": "ping",
                    "versions": [
                        "Default"
                    ]
                }
            },
            "active": true,
            "date_created": "0001-01-01T00:00:00Z",
            "hmac_enabled": true,
            "is_inactive": false,
            "key_expires_in": 3600,
            "last_updated": "1508835902",
            "name": "Default",
            "org_id": "59eee119d404630001831723",
            "partitions": {
                "acl": false,
                "quota": false,
                "rate_limit": true
            },
            "per": 60,
            "quota_max": -1,
            "quota_renewal_rate": 60,
            "rate": 1000,
            "tags": []
        },
        {
            "_id": "5a03acbd7247dd0001fa5fac",
            "access_rights": {
                "7c3a6d9d062a46ce425c7ef153be8ae6": {
                    "allowed_urls": [],
                    "apiid": "7c3a6d9d062a46ce425c7ef153be8ae6",
                    "apiname": "mytest",
                    "versions": [
                        "Default"
                    ]
                }
            },
            "active": true,
            "date_created": "0001-01-01T00:00:00Z",
            "hmac_enabled": false,
            "is_inactive": false,
            "key_expires_in": 3600,
            "last_updated": "1510190319",
            "name": "mytest",
            "org_id": "59eee119d404630001831723",
            "partitions": {
                "acl": false,
                "quota": false,
                "rate_limit": false
            },
            "per": 60,
            "quota_max": -1,
            "quota_renewal_rate": 60,
            "rate": 1000,
            "tags": []
        }
    ],
    "Pages": 0
}

```


## 检索单个策略
属性|描述
---|---
url|`/api/portal/policies/{id}`
请求方法|GET
id| policy的id
authorization| 用户的访问凭证


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X GET \
     http://127.0.0.1:3000/api/portal/policies/5a03acbd7247dd0001fa5fac | python -mjson.tool
```

**响应样例**
```json
{
    "_id": "5a03acbd7247dd0001fa5fac",
    "access_rights": {
        "7c3a6d9d062a46ce425c7ef153be8ae6": {
            "allowed_urls": [],
            "api_id": "7c3a6d9d062a46ce425c7ef153be8ae6",
            "api_name": "mytest",
            "versions": [
                "Default"
            ]
        }
    },
    "active": true,
    "date_created": "0001-01-01T00:00:00Z",
    "hmac_enabled": false,
    "id": "",
    "is_inactive": false,
    "key_expires_in": 3600,
    "last_updated": "1510190319",
    "name": "mytest",
    "org_id": "59eee119d404630001831723",
    "partitions": {
        "acl": false,
        "quota": false,
        "rate_limit": false
    },
    "per": 60,
    "quota_max": -1,
    "quota_renewal_rate": 60,
    "rate": 1000,
    "tags": []
}
```

## 创建策略
属性|描述
---|---
url|`/api/portal/policies/`
请求方法|POST
authorization| 用户的访问凭证


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -H "Content-Type: application/json" \
      -X POST \
      - d '{
               "last_updated": "0001-01-01T00:00:00Z",
               "rate": 1000,
               "per": 60,
               "quota_max": -1,
               "quota_renews": 1481546970,
               "quota_remaining": 0,
               "quota_renewal_rate": 60,
               "access_rights": {
                   "35447b1469df4e846894b1e87372f6d7": {
                       "api_id": "35447b1469df4e846894b1e87372f6d7",
                       "api_name": "My API",
                       "versions": ["Default"]
                   }
               },
               "name": "My Policy",
               "active": true
           }' http://127.0.0.1:3000/api/portal/policies/ | python -mjson.tool
```

**响应样例**
```json
    {
        "Status": "OK",
        "Message": "56b9fed54e86e40001000002",
        "Meta": "null"
    }
```

## 更新策略
属性|描述
---|---
url|`/api/portal/policies/{id}`
请求方法|PUT
id| policy的id
authorization| 用户的访问凭证


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -H "Content-Type: application/json" \
      -X PUT \
      - d '{
               "last_updated": "0001-01-01T00:00:00Z",
               "rate": 1000,
               "per": 60,
               "quota_max": -1,
               "quota_renews": 1481546970,
               "quota_remaining": 0,
               "quota_renewal_rate": 60,
               "access_rights": {
                   "35447b1469df4e846894b1e87372f6d7": {
                       "api_id": "35447b1469df4e846894b1e87372f6d7",
                       "api_name": "My API",
                       "versions": ["Default"]
                   }
               },
               "name": "My Policy",
               "active": true
           }' http://127.0.0.1:3000/api/portal/policies/56b9fed54e86e40001000002 | python -mjson.tool
```

**响应样例**
```json
  {
        "Status": "OK",
        "Message": "Data updated",
        "Meta": ""
    }
```