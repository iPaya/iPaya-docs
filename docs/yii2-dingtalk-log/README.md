# Yii 2 钉钉群机器人日志报警

文档 [DingTalk@iPayaDocs](https://github.com/iPaya/iPaya-docs/blob/master/docs/ding-talk/README.md)

## 安装

使用 `composer` 安装

```bash
composer require ipaya/yii2-dingtalk-log --prefer-dist
```

## 使用方法

在配置文件中:

```php
<?php

return [
    // ...
    'components'=>[
        'log' => [
            'traceLevel' => YII_DEBUG ? 3 : 0,
            'targets' => [
                // ...
                [
                    'class' => 'iPaya\Yii2\DingTalk\Log\Target',
                    'levels' => ['error'],
                    'accessToken' => '<你的钉钉聊天机器人 Access Token>',
                    'title' => '程序日志', // 自定义的消息标题
                ],
                // ...
            ],
        ],
    ]
    // ...
];
```

## 如何获取钉钉聊天机器人 Access Token

参见 [钉钉官方文档](https://open-doc.dingtalk.com/docs/doc.htm?treeId=257&articleId=105735&docType=1)

