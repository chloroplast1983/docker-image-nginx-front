## HTTPS

这个镜像是基于`HTTP`, 因为我们的CA这一层是放在前端代理层上处理.

如果需要考虑`https`的安全性, 需要添加如下`header`:

* `Strict-Transport-Security`

### Strict-Transport-Security

#### 概述

一个网站接受一个`HTTP`的请求, 然后跳转到`HTTPS(302)`, 用户可能在开始跳转前, 通过没有加密的方式和服务器对话. 如: 输入http://www.abc.com, 然后跳转到https://www.abc.com.

这样存在中间人攻击潜在威胁, 跳转过程可能被恶意网站利用来直接接触用户信, 而不是原来的加密信息.

网站通过`HTTP Strict Transport Security`通知浏览器, 这个网站禁止使用HTTP方式加载, 浏览器应该自动把所有尝试使用HTTP的请求自动替换为`HTTPS`请求.

#### 参数

* `max-age=<expire-time>`: 浏览器记录应当使用`HTTPS`访问网站的时间, 单位是秒.
* `includeSubDomains`: 是否对二级域名也适用.

#### 示例

```
add_header Strict-Transport-Security: max-age=31536000; includeSubDomains
```

所有现有域名以及未来的二级域名将会使用`HTTPS`最多1年. 防止浏览器使用`HTTP`协议访问.