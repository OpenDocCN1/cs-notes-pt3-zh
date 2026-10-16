# MIME支持的数据类型

| 类型 | 子类型 | 含义描述 |
|---|---|---|
| Text | Plain | 无格式文本 |
| Text | Richttext | 有简单格式的文本 |
| Image | Gif | GIF格式静态图像 |
| Image | Jpeg | JPEG格式静态图像 |
| Audio | Basic | 音频 |
| Video | Mpeg | MPEG格式视频 |
| Application | octet-stream | 字节序列 |
| Application | Postscript | PostScript 文档 |
| Message | RFC5322 | RFC 5322格式的消息 |
| Message | Partial | 部分消息（消息被拆分，以便于传输） |
| Message | External-body | 访问外部数据的机制（访问方法、URL等） |
| Multipart | Mixed | 消息的多个独立部分按顺序组织在一起 |
| Multipart | Alternative | 相同消息的另一种格式 |
| Multipart | Parallel | 消息的多个部分必须同步 |
| Multipart | Digest | 每个部分都是完整的RFC 5322消息 |