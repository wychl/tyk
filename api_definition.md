## api定义
### 常用配置
- name  api名字
- api_id api唯一标识
- slug
- org_id api和api key 拥有者的身份标识
- active 设置为false时 在启动，重新启动或者重新加载时该api的所有路由不再代理 
- session_lifetime 设置api的session过期时间
### 身份认证模式
- Auth Token 默认
- JWT
- HMAC
- OAuth2.0
- Basic Auth
- Open ID Connect
- Use Custom Auth(plugin)
- Use Multiple Auth Mechanisms
- Open Keyless

### api版本化
版本化api，不同版本的api应用不同的策略

- not_versioned 是否版本化api     
- location 版本信息位置  header；url-param；第一个url参数(/v1/resource/id)
- key 版本信息的key
- expires 过期日期，默认永远不过器

### endpoint
- global_headers 设置全局header
- global_headers_remove 移除所有请求指定的header

### ip白名单
- enable_ip_whitelisting 是否启用白名单
- allowed_ips 被允许访问tyk的api地址

### CORS
- enable 启用cors
- allowed_origins 允许访问的域名
- allowed_methods 允许的请求方式
- allowed_headers 请求中允许的headers
- exposed_headers 响应中的headers
- allow_credentials 是否允许凭证(cookie)
- max_age 凭证过期时间
- options_passthrough 是否允许options请求方式
    

### proxy
- listen_path: tyk监听的path,
- target_url: 自己服务的url,
- strip_listen_path 设置为true时，tyk移除请求中的listen_path，从而不影响服务的路由
- enable_load_balancing 启用负载均衡
- target_list 启用负载均衡时可以在target_list中加服务多个实例的url
- 服务发现
    - use_discovery_service 启用服务发现，默认不启用
    - query_endpoint
    - use_nested_query
    - parent_data_path
    - data_path
    - port_data_path
    - use_target_list
    - cache_timeout
    - endpoint_returns_list

### 批量请求
- enable_batch_request_support 启用批量请求 默认不启用

### 白名单
- enable_ip_whitelisting 启用白名单 默认不起用
- allowed_ips 添加允许访问的ip(比如 docker容器的Gateway地址)

### 缓存中间件 cache_options
- enable_cache 启用缓存，默认启用
- enable_upstream_cache_control 启用自己服务的缓存
- cache_timeout 缓存过期时间
- cache_all_safe_requests

### tags
- 给定义的api添加tag

### 事件 event_handlers

## rest api 创建api
```json
    //POST /tyk/apis/ HTTP/1.1
    //Host: localhost:8080
    //Connection: keep-alive
    //Content-Length: 739
    //Pragma: no-cache
    //Cache-Control: no-cache

    {
        "id": "55780c119b23c3000100004f",
        "name": "HttpBin",
        "slug": "httpbin",
        "api_id": "2fdd8512a856434a61f080da67a88851",
        "org_id": "55780af69b23c30001000000",
        "use_keyless": true,
        "use_oauth2": false,
        "oauth_meta": {
            "allowed_access_types": [],
            "allowed_authorize_types": [],
            "auth_login_redirect": ""
        },
        "auth": {
            "use_param": false,
            "use_cookie": false,
            "auth_header_name": ""
        },
        "use_basic_auth": false,
        "enable_jwt": false,
        "jwt_signing_method": "",
        "notifications": {
            "shared_secret": "",
            "oauth_on_keychange_url": ""
        },
        "enable_signature_checking": false,
        "hmac_allowed_clock_skew": -1,
        "definition": {
            "location": "header",
            "key": "x-api-version"
        },
        "version_data": {
            "not_versioned": true,
            "versions": {
                "Default": {
                    "name": "Default",
                    "expires": "",
                    "paths": {
                        "ignored": [],
                        "white_list": [],
                        "black_list": []
                    },
                    "use_extended_paths": true,
                    "extended_paths": {
                        "ignored": [],
                        "white_list": [],
                        "black_list": [],
                        "cache": [],
                        "transform": [],
                        "transform_response": [],
                        "transform_headers": [],
                        "transform_response_headers": [],
                        "hard_timeouts": [],
                        "circuit_breakers": [],
                        "url_rewrites": [],
                        "virtual": [],
                        "size_limits": []
                    },
                    "global_headers": {},
                    "global_headers_remove": [],
                    "global_size_limit": 0
                }
            }
        },
        "uptime_tests": {
            "check_list": [],
            "config": {
                "expire_utime_after": 0,
                "service_discovery": {
                    "use_discovery_service": false,
                    "query_endpoint": "",
                    "use_nested_query": false,
                    "parent_data_path": "",
                    "data_path": "",
                    "port_data_path": "",
                    "use_target_list": false,
                    "cache_timeout": 0,
                    "endpoint_returns_list": false
                },
                "recheck_wait": 0
            }
        },
        "proxy": {
            "listen_path": "/test/",
            "target_url": "http://httpbin.org/",
            "strip_listen_path": true,
            "enable_load_balancing": false,
            "target_list": [],
            "check_host_against_uptime_tests": false,
            "service_discovery": {
                "use_discovery_service": false,
                "query_endpoint": "",
                "use_nested_query": false,
                "parent_data_path": "",
                "data_path": "",
                "port_data_path": "",
                "use_target_list": false,
                "cache_timeout": 0,
                "endpoint_returns_list": false
            }
        },
        "custom_middleware": {
            "pre": [],
            "post": [],
            "response": []
        },
        "cache_options": {
            "cache_timeout": 60,
            "enable_cache": true,
            "cache_all_safe_requests": false,
            "enable_upstream_cache_control": false
        },
        "session_lifetime": 0,
        "active": true,
        "auth_provider": {
            "name": "",
            "storage_engine": "",
            "meta": {}
        },
        "session_provider": {
            "name": "",
            "storage_engine": "",
            "meta": null
        },
        "event_handlers": {
            "events": {}
        },
        "enable_batch_request_support": false,
        "enable_ip_whitelisting": false,
        "allowed_ips": [],
        "dont_set_quota_on_create": false,
        "expire_analytics_after": 0,
        "response_processors": [],
        "CORS": {
            "enable": false,
            "allowed_origins": [],
            "allowed_methods": [],
            "allowed_headers": [],
            "exposed_headers": [],
            "allow_credentials": false,
            "max_age": 0,
            "options_passthrough": false,
            "debug": false
        },
        "domain": "",
        "tags": []
    }
```