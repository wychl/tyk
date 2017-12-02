## policy

安全策略包含公共api的所有信息

- 速率限制
- 配额
- 访问列表（哪些api或者哪些api版本被允许访问）
- 粒度访问（哪些方法和路径允许）
- 多个token的管理（使用policy可以管理成千上万个token）

**更新token访问级别时，只需要替换token的policy即可**