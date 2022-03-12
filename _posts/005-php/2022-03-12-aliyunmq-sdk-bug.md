---
layout: post
title: aliyunmq http sdk php组件依赖问题解决方案
description: aliyunmq http sdk php组件依赖问题解决方案
category: 005-php
---

> 问题简述：aliyunmq/mq-http-sdk 最新版1.0.1 内部依赖问题导致的服务异常情况处理


```
目前使用的是aliyunmq/mq-http-sdk最新版1.0.1  
依赖包 guzzlehttp/guzzle: >=6.0.0  

https://packagist.org/packages/aliyunmq/mq-http-sdk

1.0.1
requires

php: >=5.5.0
guzzlehttp/guzzle: >=6.0.0

```


```
但目前 guzzlehttp/guzzle 最新版是 7.2.0   

https://packagist.org/packages/guzzlehttp/guzzle

7.2.0
requires

php: ^7.2.5 || ^8.0
ext-json: *
guzzlehttp/promises: ^1.4
guzzlehttp/psr7: ^1.7
psr/http-client: ^1.0

```


```
aliyunmq/mq-http-sdk composer.json

{
    "name": "aliyunmq/mq-http-sdk",
    "type": "library",
    "description": "Aliyun Message Queue(MQ) Http PHP SDK, PHP>=5.5.0",
    "keywords": ["Aliyun","Alicloud", "MQ", "Message Queue", "Message", "Queue"],
    "homepage": "https://github.com/aliyunmq/mq-http-php-sdk",
    "license": "MIT",
    "require": {
        "php": ">=5.5.0",
        "guzzlehttp/guzzle": ">=6.0.0"
    },
    "repositories": {
        "packagist": {
            "type": "composer",
            "url": "https://packagist.phpcomposer.com"
        }
    },
    "autoload":{
        "psr-4": {
            "MQ\\": "MQ/"
        }
    }
}

```

```
aliyunmq/mq-http-sdk 1.0.1 不兼容 7.2.0

错误日志：
[2020-10-16 16:27:28] production.ERROR: Symfony\Component\Debug\Exception\FatalThrowableError: Undefined class constant 'VERSION' in /data/op_db/vendor/aliyunmq/mq-http-sdk/MQ/Http/HttpClient.php:50
```

解决方法：
```
根据错误提示找到那一行：
$this->agent = "mq-php-sdk/1.0.1(GuzzleHttp/" . \GuzzleHttp\Client::VERSION . " PHP/" . PHP_VERSION . ")";

修改为：

$this->agent = "mq-php-sdk/1.0.1(GuzzleHttp/" . \GuzzleHttp\Client::MAJOR_VERSION . " PHP/" . PHP_VERSION . ")";
```