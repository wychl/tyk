## Basic Auth
Basic Auth 是api的token一种形式，生成的token值是不变


## 创建一个用户

**参数：**

- user_name
- password
- api_id
- api_name 

属性|描述
---|---
url|`/api/apis/keys/basic/{username}`
请求方法|POST
authorization| 用户的访问凭证

**请求样例**
```bash
curl -X POST -H "authorization: 859cdd67aacb42c0750162ce6ac39ab3" \
     -s \
     -H "Content-Type: application/json" \
     -X POST \
     -d '{
        "last_check": 0,
        "allowance": 1000,
        "rate": 1000,
        "per": 60,
        "expires": 0,
        "quota_max": 10000,
        "quota_renews": 1424543479,
        "quota_remaining": 10000,
        "quota_renewal_rate": 2520000,
        "access_rights": {
            "9814e00125194b1d7321ee8fcb4baae3": {
                "api_id": "9814e00125194b1d7321ee8fcb4baae3",
                "api_name": "Test",
                "versions": [
                    "Default"
                ]
            }
        },
        "basic_auth_data": {
            "password": "test123"
    }
    }' http://127.0.0.1:3000/api/apis/keys/basic/xiaoming | python -mjson.tool
```

**响应样例**

```json
{
    "api_model": {},
    "key_id": "5a0bb9b973169000018c7931xiaoming",
    "data": {
        "last_check": 0,
        "allowance": 1000,
        "rate": 1000,
        "per": 60,
        "expires": 0,
        "quota_max": 10000,
        "quota_renews": 1424543479,
        "quota_remaining": 10000,
        "quota_renewal_rate": 2520000,
        "access_rights": {
            "9814e00125194b1d7321ee8fcb4baae3": {
                "api_name": "Test",
                "api_id": "9814e00125194b1d7321ee8fcb4baae3",//api的api_id
                "versions": [
                    "Default"
                ],
                "allowed_urls": null
            }
        },
        "org_id": "5a0bb9b973169000018c7931",
        "oauth_client_id": "",
        "basic_auth_data": {
            "password": "test123",
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
        "meta_data": null,
        "tags": null,
        "alias": "",
        "last_updated": ""
    }
}
```

**注意**：key_id api的访问token

**测试api**
```bash
    curl -H "Authorization:59eee119d4046300018317230b2a578fab4842fe5966a0e2633e55fd" http://127.0.0.1/mytest/