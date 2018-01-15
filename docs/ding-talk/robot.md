# 群机器人

> 官网文档: [钉钉开发平台](https://open-doc.dingtalk.com/docs/doc.htm?treeId=257&articleId=105733&docType=1)

## 初始化

```php
<?php
use iPaya\DingTalk\Client;

$dingTalk = new Client();
$robot = $dingTalk->robot()->configure('官方群聊机器人生成的 Access Token');
```

## 发送消息

### 发送文本消息

```php
<?php

$content = '大家好，我是自定义的钉钉群聊机器人 iPayaRobot。';
$at = null;

$robot->sendText($content, $at);
```

**参数**:

- `$content`: 必填，消息内容
- `$at`: 选填，默认 `null`, 被@的人手机号数组，@所有人请设置为 `*`

## 发送 Link 类型消息

```php
<?php

$title = '标题';
$content = '内容';
$url = 'https://github.com/iPaya/dingtalk';
$picUrl = null;
$robot->sendLink($title, $content, $url, $picUrl);
```

**参数**:

- `$title`: 必填, 消息标题
- `$content`: 必填, 消息内容。消息太长只会部分显示
- `$url`: 必填, 点击消息后跳转的 URL
- `$picUrl`: 选填, 默认 `null`, 图片 URL

## 发送 Markdown 类型消息

```php
<?php

$title = '标题';
$content = '内容';
$at = null;
$robot->sendMarkdown($title, $content, $at);
```

**参数**:

- `$title`: 必填, 消息标题
- `$content`: 必填, Markdown 消息内容
- `$at`: 选填，默认 `null`, 被@的人手机号数组，@所有人请设置为 `*`

> 注意: Markdown 目前只支持 Markdown 语法的子集

## 发送整体跳转的 ActionCard 类型消息

```php
<?php

$title = '标题';
$content = '内容';
$singleTitle = '';
$url = '';
$hideAvatar = false;

$robot->sendSingleActionCard($title, $content, $singleTitle, $url, $hideAvatar);
```

**参数**:

- `$title`: 必填, 消息标题
- `$content`: 必填, 消息内容
- `$singleTitle`: 必填, 底部显示的跳转按钮标题
- `$singleUrl`: 必填, 点击后的跳转 URL
- `$hideAvatar`: 选填，默认 `false`, 是否隐藏发消息者头像

## 发送独立跳转的 ActionCard 类型消息

```php
<?php

$title = '标题';
$content = '内容';
$buttons = [
    ['title' => '按钮 1', 'url' => 'https://github.com/iPaya/dingtalk'],
    ['title' => '按钮 2', 'url' => 'https://github.com/iPaya/dingtalk'],
];
$hideAvatar = false;
$btnOrientation = 0;

$robot->sendActionCard($title, $content, $buttons, $hideAvatar, $btnOrientation);
```

**参数**:

- `$title`: 必填, 消息标题
- `$content`: 必填, 消息内容
- `$buttons`: 必填，按钮数组
- `$hideAvatar`: 选填，默认 `false`, 是否隐藏发消息者头像
- `$btnOrientation`: 选填, 默认 `0`, 0 表示竖直排列按钮, 1 表示横向排列按钮

## 发送 FeedCard 类型消息

```php
<?php

$links = [
    ['title' => '标题一', 'url' => 'https://github.com/iPaya/dingtalk', 'picUrl' => 'https://wxt.sinaimg.cn/thumb300/6a5cfb7bgy1fgidkr34hpj21kw11xh2e.jpg'],
    ['title' => '标题二', 'url' => 'https://github.com/iPaya/dingtalk', 'picUrl' => 'https://wxt.sinaimg.cn/thumb300/6a5cfb7bgy1fgidkr34hpj21kw11xh2e.jpg'],
    ['title' => '标题三', 'url' => 'https://github.com/iPaya/dingtalk', 'picUrl' => 'https://wxt.sinaimg.cn/thumb300/6a5cfb7bgy1fgidkr34hpj21kw11xh2e.jpg'],
];

$robot->sendFeedCard($links);
```

**参数**:

- `$links`: 必填, 消息列表
- `$links[]['title']`: 必填, 标题
- `$links[]['url']`: 必填, 链接 URL
- `$links[]['picUrl']`: 必填, 图片 URL
