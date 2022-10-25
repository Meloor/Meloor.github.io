---
title: http请求返回状态码
date: 2020-12-03 22:07:49
tags: [http]
categories:
    - web
    - web
---

参考博客：
* [HTTP请求返回状态码详解](https://blog.csdn.net/wangsen2235068/article/details/8081274)
* [常用的HTTP状态码(面试中常问到...)](https://blog.csdn.net/beyond150/article/details/102128827)

## 首先，什么是状态码？
状态码的职责是当客户端向服务器端发送请求时，描述返回的请求结
果。借助状态码，用户可以知道服务器端是正常处理了请求，还是出
现了错误。
## 接着来，状态码有哪些种类？
![状态码](http请求返回状态码/1.png)
接下来我们详细说一说常用的状态码（背吧，别犹豫）
## 2XX 成功
200 ok（请求成功）
204 no content （请求成功，但是没有结果返回）
206 partial content （客户端请求一部分资源，服务端成功响应，返回一范围资源）?
## 3XX 重定向
301 move permanently （永久性重定向）
302 found （临时性重定向）
303 see other （示由于请求对应的资源存在着另一个 URI，应使用 GET
方法定向获取请求的资源）
304 not modified （表示在客户端采用带条件的访问某资源时，服务端找到了资源，但是这个请求的条件不符合。跟重定向无关）
307 temporary redirect （跟302一个意思）
## 4XX 客户端错误
400 bad request （请求报文存在语法错误）
401 unauthorized （需要认证（第一次返回）或者认证失败（第二次返回））
403 forbidden （请求被服务器拒绝了）
404 not found （服务器上无法找到请求的资源）
## 5XX 服务器错误
500 internal server error （服务端执行请求时发生了错误）
503 service unavailable （服务器正在超负载或者停机维护，无法处理请求）