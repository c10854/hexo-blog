---
title: Yar学习笔记
date: 2017-09-04 22:26:20
tags: PHP
---
### 什么是RPC
RPC是指远程过程调用，也就是说如果一台服务器想要调用其它服务器的应用上存在的方法，因为两台服务器本身不是使用的同一个内存空间，所以不能直接调用，需要通过网络来表达调用的语义和传达调用的数据。
### Yar
Yar是一个轻量级、高效的RPC框架，提供了一种简单方法来让PHP项目之间可以互相远程调用对方的本地方法。同事Yar提供了并行调用简单能力，支持同时调用多个远程服务的方法。
## server端写法
```php
<?php
class API {
    /**
     * the doc info will be generated automatically into service info page.
     * @params
     * @return
     */
    public function api($parameter, $option = "foo") {
    }

    protected function client_can_not_see() {
    }
}

$service = new Yar_Server(new API());
$service->handle();
?>
```
## client端写法
```php
<?php
$client = new Yar_Client("http://houst/api");
$result = $client->api("parameter");
?>
```
## 并行化调用
```php
<?php
function callback($retval, $callinfo) {
     var_dump($retval);
}

Yar_Concurrent_Client::call("http://host/api/", "api", array("parameters"), "callback");
Yar_Concurrent_Client::call("http://host/api/", "api", array("parameters"), "callback");
Yar_Concurrent_Client::call("http://host/api/", "api", array("parameters"), "callback");
Yar_Concurrent_Client::call("http://host/api/", "api", array("parameters"), "callback");
Yar_Concurrent_Client::loop(); //send
?>
```