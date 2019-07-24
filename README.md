# docker-image-nginx-front

---

## 简介

默认前端服务专用`nginx`配置. 主要核心针对互联网接口调用. 负责生成`token`, 用于记录日之链.

## 关于https

[关于https](./Docs/https.md)的一些配置项说明.

## 版本

* [1.0](./Docs/1.0.md)
	* [1.1](./Docs/1.1.md)
	* [1.2](./Docs/1.2.md)
	* [1.3](./Docs/1.3.md)
	* [1.4](./Docs/1.4.md)

#### 浏览器如何处理

你的网站第一次通过HTTPS请求, 服务器响应`Strict-Transport-Security`头, 浏览器记录下这些信息, 然后后面尝试访问这个网站的请求都会自动把HTTP替换为HTTPS.

当`HSTS头`设置的过期时间到了, 后面通过`HTTP`的访问恢复到正常模式, 不会再自动跳转到HTTPS.

每次浏览器接收到`Strict-Transport-Security`头, 它都会更新这个网站的过期时间, 所以网站可以刷新这些信息, 防止过期发生.

## todolist

### fastCGI参数优化

* `fastcgi_connect_timeout`: 指定连接到后端FastCGI的超时时间.
* `fastcgi_send_timeout`: 指定向FastCGI传送请求的超时时间.
* `fastcgi_read_timeout`: 指定接收FastCGI应答的超时时间.这个值是已经完成两次握手后接收FastCGI应答的超时时间

配套需要调整`phpfpm`中`ini`文件的`max_execution_time`.和`www.conf`中的`request_terminate_timeout`. 并且确认之间的关系影响.