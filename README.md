# docker-image-nginx-front

---

## 简介

默认前端服务专用`nginx`配置. 主要核心针对互联网接口调用. 负责生成`token`, 用于记录日之链.

## 版本

* [1.0](./Docs/1.0.md)
	* [1.1](./Docs/1.1.md)
	* [1.2](./Docs/1.2.md)

## todolist

### fastCGI参数优化

* `fastcgi_connect_timeout`: 指定连接到后端FastCGI的超时时间.
* `fastcgi_send_timeout`: 指定向FastCGI传送请求的超时时间.
* `fastcgi_read_timeout`: 指定接收FastCGI应答的超时时间.这个值是已经完成两次握手后接收FastCGI应答的超时时间

配套需要调整`phpfpm`中`ini`文件的`max_execution_time`.和`www.conf`中的`request_terminate_timeout`. 并且确认之间的关系影响.