# HTTP 响应：状态码（RFC2616）

| 状态码 | 简短解释 | 含义 |
|---|---|---|
| 200 | OK | 网页请求成功，消息体包含所请求的数据 |
| 204 | No content | 网页请求成功，但无需返回消息体，网页不用刷新，例如对用户提交信息的确认 |
| 301 | Moved Permanently | 请求内容已经移到另一个服务器，响应的消息头中将包含该服务器的域名 |
| 304 | Not Modified | 网页没有修改，用户可以继续使用缓存的网页，此响应中不包含消息体 |
| 403 | Forbidden | 用户没有权限访问请求的网页 |
| 404 | Not found | 没有找到请求网页，可能是由于用户提供的URL错误 |
| 500 | Internal Server Error | 服务器内部故障 |
| 503 | Service Unavailable | 服务器由于临时过载，不能响应用户的请求 |
| 505 | HTTP Version Not Supported | 服务器不支持请求消息中的HTTP版本 |