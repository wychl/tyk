## token策略

- 一个pokicy可以应用多个api
- Rate limits 访问速率的控制 比如平均一秒访问几次
- Usage Quotas 访问配额，一个小时以内访问次数
- 设置token的过期时间（基于该policy创建的token），默认永远不过期
- is_inactive 为true时，所有使用该policy的token无效，返回值："Key is inactive, please renew"
- 基于path的访问控制，控制每个path允许的请求方法   

## 获取policy列表

属性|描述
---|---
url|`/api/portal/policies/`
请求方法|GET
authorization| 用户的访问凭证

**注意：** tyk.conf的hash_keys为true时该api不起作用,


**请求样例**
```bash
curl -H "authorization: 5191604d97ff4ecf699293039c124f72" \
      -X GET \
     http://127.0.0.1:3000/api/portal/policies/
```
**响应样例**
```json
    {
    "Data": [
        {
            "_id": "5a0d2df0731690000132f591",
            "access_rights": {
                "9814e00125194b1d7321ee8fcb4baae3": {
                    "allowed_urls": [],
                    "apiid": "9814e00125194b1d7321ee8fcb4baae3",
                    "apiname": "test2",
                    "versions": [
                        "Default"
                    ]
                }
            },
            "active": true,
            "date_created": "0001-01-01T00:00:00Z",
            "hmac_enabled": false,
            "is_inactive": false,
            "key_expires_in": 0,
            "last_updated": "1510813281",
            "name": "test2 Policy",
            "org_id": "5a0bb9b973169000018c7931",
            "partitions": {
                "acl": false,
                "quota": false,
                "rate_limit": false
            },
            "per": 60,
            "quota_max": -1,
            "quota_renewal_rate": 60,
            "rate": 3,
            "tags": []
        }
    ],
    "Pages": 0
}
```


## 检索特定策略

属性|描述
---|---
url|`/api/portal/policies/{id}`
请求方法|GET
authorization| 用户的访问凭证

**请求样例**
```bash
curl -H "authorization: 5191604d97ff4ecf699293039c124f72" \
      -X GET \
     http://127.0.0.1:3000/api/portal/policies/5a0d2df0731690000132f591

```

**响应样例**
```json
{
    "_id": "5a0d2df0731690000132f591",
    "id": "",
    "org_id": "5a0bb9b973169000018c7931",
    "rate": 3,
    "per": 60,
    "quota_max": -1,
    "quota_renewal_rate": 60,
    "access_rights": {
        "9814e00125194b1d7321ee8fcb4baae3": {
            "api_name": "test2",
            "api_id": "9814e00125194b1d7321ee8fcb4baae3",
            "versions": [
                "Default"
            ],
            "allowed_urls": []
        }
    },
    "hmac_enabled": false,
    "active": true,
    "name": "test2 Policy",
    "is_inactive": false,
    "date_created": "0001-01-01T00:00:00Z",
    "tags": [],
    "key_expires_in": 0,
    "partitions": {
        "quota": false,
        "rate_limit": false,
        "acl": false
    },
    "last_updated": "1510813281"
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
curl -X POST -H "authorization: 5191604d97ff4ecf699293039c124f72" \
     -s \
     -H "Content-Type: application/json" \
     -X POST \
     -d ' {
        "last_updated": "0001-01-01T00:00:00Z",
        "rate": 1000,
        "per": 60,
        "quota_max": -1,
        "quota_renews": 1481546970,
        "quota_remaining": 0,
        "quota_renewal_rate": 60,
        "access_rights": {
            "9814e00125194b1d7321ee8fcb4baae3": {
                "api_id": "9814e00125194b1d7321ee8fcb4baae3",
                "api_name": "test2",
                "versions": ["Default"]
            }
        },
        "name": "test2 Policy",
        "active": true
    }    'http://127.0.0.1:3000/api/portal/policies/ | python -mjson.tool
```

**响应样例**

```json
{
    "Status": "OK",
    "Message": "5a0d359a731690000132f592",
    "Meta": null
}
```
