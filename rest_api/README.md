## rest api

要使用 rest api tyk.conf的use_db_app_configs配置为false

创建的api会以{api-id}.json文件的形式写到app_path目录中

多个tyk实例运行时，需要在不同节点独立更新api配置


[rest-api文档](https://tyk.io/docs/tyk-rest-api/)