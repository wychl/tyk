## 获取key列表

属性|描述
---|---
url|`/api/apis/{api-id}}/keys`
请求方法|GET
authorization| 用户的访问凭证

**注意：** tyk.conf的hash_keys为true时该api不起作用,


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X GET \
     http://127.0.0.1:3000/api/apis/7c3a6d9d062a46ce425c7ef153be8ae6/keys
```
**响应样例**
```json
    {
        "data": {
            "keys": [
                "59eee119d404630001831723d5ec9be88f684db94b4f9c38f645c38f"
            ]
        },
        "pages": 0
    }
```


## 检索特定key

属性|描述
---|---
url|`/api/apis/{api-id}}/keys/{key-id}`
请求方法|GET
authorization| 用户的访问凭证

**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X GET \
     http://127.0.0.1:3000/api/apis/7c3a6d9d062a46ce425c7ef153be8ae6/keys/59eee119d404630001831723d5ec9be88f684db94b4f9c38f645c38f

```

**响应样例**
```json
{
    "api_model": {},
    "key_id": "59eee119d404630001831723d5ec9be88f684db94b4f9c38f645c38f",
    "data": {
        "last_check": 0,
        "allowance": 1000,
        "rate": 1000,
        "per": 1,
        "expires": -1,
        "quota_max": -1,
        "quota_renews": 1510046082,
        "quota_remaining": -1,
        "quota_renewal_rate": 60,
        "access_rights": {
            "7c3a6d9d062a46ce425c7ef153be8ae6": {
                "api_name": "mytest",
                "api_id": "7c3a6d9d062a46ce425c7ef153be8ae6",
                "versions": [
                    "Default"
                ],
                "allowed_urls": null
            }
        },
        "org_id": "59eee119d404630001831723",
        "oauth_client_id": "",
        "basic_auth_data": {
            "password": "",
            "hash_type": ""
        },
        "jwt_data": {
            "secret": ""
        },
        "hmac_enabled": false,
        "hmac_string": "",
        "is_inactive": false,
        "apply_policy_id": "",
        "data_expires": 0,
        "monitor": {
            "trigger_limits": null
        },
        "meta_data": {},
        "tags": null,
        "alias": "",
        "last_updated": "1510046022"
    }
}
```


## 创建key

属性|描述
---|---
url|`/api/keys`
请求方法|POST
authorization| 用户的访问凭证

**请求样例**
```bash
curl -X POST -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
     -s \
     -H "Content-Type: application/json" \
     -X POST \
     -d '{
        "allowance": 1000,
        "rate": 1000,
        "per": 1,
        "expires": -1,
        "quota_max": -1,
        "quota_renews": 1449051461,
        "quota_remaining": -1,
        "quota_renewal_rate": 60,
        "access_rights": {
            "7c3a6d9d062a46ce425c7ef153be8ae6": {
                "api_id": "7c3a6d9d062a46ce425c7ef153be8ae6",
                "api_name": "mytest",
                "versions": ["Default"]
            }
        },
        "meta_data": {}
     }' http://localhost:3000/api/keys | python -mjson.tool
```

**响应样例**

```json
{
    "api_model": {},
    "data": {
        "access_rights": {
            "7c3a6d9d062a46ce425c7ef153be8ae6": {
                "allowed_urls": null,
                "api_id": "7c3a6d9d062a46ce425c7ef153be8ae6",
                "api_name": "mytest",
                "versions": [
                    "Default"
                ]
            }
        },
        "alias": "",
        "allowance": 1000,
        "apply_policy_id": "",
        "basic_auth_data": {
            "hash_type": "",
            "password": ""
        },
        "data_expires": 0,
        "expires": -1,
        "hmac_enabled": false,
        "hmac_string": "",
        "is_inactive": false,
        "jwt_data": {
            "secret": ""
        },
        "last_check": 0,
        "last_updated": "1510296894",
        "meta_data": {},
        "monitor": {
            "trigger_limits": null
        },
        "oauth_client_id": "",
        "org_id": "59eee119d404630001831723",
        "per": 1,
        "quota_max": -1,
        "quota_remaining": -1,
        "quota_renewal_rate": 60,
        "quota_renews": 1510296954,
        "rate": 1000,
        "tags": null
    },
    "key_id": "59eee119d4046300018317230b2a578fab4842fe5966a0e2633e55fd"
}
```

**注意**：key_id api的访问token

**测试api**
```bash
    curl -H "Authorization:59eee119d4046300018317230b2a578fab4842fe5966a0e2633e55fd" http://127.0.0.1/mytest/
```

## 更新key
属性|描述
---|---
url|`/api/apis/{{apiId}}/keys/{{keyId}}`
请求方法|PUT
authorization| 用户的访问凭证


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X PUT \
     http://127.0.0.1:3000/api/apis/7c3a6d9d062a46ce425c7ef153be8ae6/keys/59eee119d404630001831723d5ec9be88f684db94b4f9c38f645c38f
```

**响应样例**
```json
 {
         "last_check": 0,
         "allowance": 1000,
         "rate": 1000,
         "per": 60,
         "expires": 1422113671,
         "quota_max": -1,
         "quota_renews": 1421675253,
         "quota_remaining": -1,
         "quota_renewal_rate": 60,
         "access_rights": {
             "39d2c98be05c424371c600bd8b3e2242": {
                 "api_id": "39d2c98be05c424371c600bd8b3e2242",
                 "api_name": "Nitrous Test",
                 "versions": [
                     "Default"
                 ]
             }
         },
         "org_id": "54b53d3aeba6db5c35000002",
         "oauth_client_id": "",
         "basic_auth_data": {
             "password": ""
         },
         "hmac_enabled": false,
         "hmac_string": ""
     }
```

## 删除key
属性|描述
---|---
url|`/api/apis/{api-id}/keys/{keyId}`
请求方法|DELETE
authorization| 用户的访问凭证


**请求样例**
```bash
curl -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
      -X DELETE \
     http://127.0.0.1:3000/api/apis/7c3a6d9d062a46ce425c7ef153be8ae6/keys/59eee119d404630001831723d5ec9be88f684db94b4f9c38f645c38f
```

**响应样例**
```json
 {
        "Status": "OK",
        "Message": "Key deleted succesfully",
        "Meta": ""
    }
```