# 为developer生成api的访问token

## 创建一个developer
 dashboard 创建


## 向developer添加一个api


属性|描述
---|---
url|`/api/portal/developers/{id}`
请求方法|PUT
authorization| 用户的访问凭证

**请求示例**
```json
 {
            "id": "5a13830f73169000018627a7",
            "api_keys": {
            "9814e00125194b1d7321ee8fcb4baae3":"90568dfa" // api的api_id
            },
            "date_created": "2017-11-21T01:36:15.045Z",
            "email": "615829168@qq.com",
            "fields": {},
            "inactive": false,
            "nonce": "",
            "org_id": "5a0bb9b973169000018c7931",
            "password": "$2a$10$fjJxMm0uCVypgrLlJtWeN./RL.9GkbqrhS.T5Fid6nqMkCSaeqiwq",
            "sso_key": "",
            "subscriptions": {}
 }
```

**返回示例**
```json
{
    "Status": "OK",
    "Message": "5a167ae61d7729000116c8f5",
    "Meta": null
}
```

## 创建生成key的请求
属性|描述
---|---
url|`/api/portal/requests`
请求方法|POST
authorization| 用户的访问凭证
id| request的id

**请求示例**
```json
{
   "by_user": "5a13830f73169000018627a7", //developer的id
   "for_plan": "5a0d2df0731690000132f591" //policy 的id    
}
```

**返回示例**

```json
{
    "Status": "OK",
    "Message": "5a166d2c1d7729000116c8f4",
    "Meta": null
}
```


## 生成key请求的列表
属性|描述
---|---
url|`/api/portal/requests`
请求方法|GET
authorization| 用户的访问凭证


**返回示例**

```json
 {
     "Data": [
         {
             "_id": "5a166d2c1d7729000116c8f4",//request id
             "approved": false,//状态
             "by_user": "5a13830f73169000018627a7",//developer id
             "date_created": "0001-01-01T00:00:00Z",
             "fields": {},
             "for_api": "",
             "for_plan": "5a0d2df0731690000132f591",//policy id
             "jwt_secret": "",
             "org_id": "5a0bb9b973169000018c7931",
             "version": ""
         }
     ],
     "Pages": 1
 }
```

## 审核生成key的请求
- 自动审核
- 用户审核
- 交给第三方系统管理（付费和额外的用户认证）


**用户审核**

属性|描述
---|---
url|`/api/portal/requests/approve/{id}`
请求方法|PUT
authorization| 用户的访问凭证
id| request的id


**返回示例**

```json
{
    "RawKey": "5a0bb9b973169000018c79314442f59f24cd4c416f1758185eab1931",//返回api访问token
    "Password": ""
}
```