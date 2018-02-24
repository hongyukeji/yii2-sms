# Yii2 短信扩展组件 - [鸿宇科技](http://www.hongyuvip.com/)

> Yii2 短信扩展组件，目前支持阿里短信、云片短信，设置默认短信，会自动切换短信发送方式。

> 碎碎念：没啥好说的，别人写的扩展组件总是没有自己写的用起来顺手。方便自己，造福他人。

## 安装

```
$ composer require hongyukeji/yii2-sms
```

## 配置

* main.php / web.php 

> 阿里短信配置参数获取教程 https://help.aliyun.com/document_detail/59210.html

> 云片短信配置参数获取教程 https://www.yunpian.com/doc/zh_CN/introduction/demos/php.html

```
'components' => [

    ```
    'sms' => [
        'class' => 'HongYuKeJi\Components\Sms\SendSms',
        'config' => [
            'default' => 'aliSms',    // 默认短信
            'aliSms' => [
                'accessKeyId' => '',
                'accessKeySecret' => '',
                'signName' => '',
                'templateCode' => [
                    'verificationCode' => '',
                ],
            ],
            'yunpianSms' => [
                'apikey' => '',
                'signName' => '',
                'templateCode' => [
                    'verificationCode' => '',
                ],
            ],
        ],
    ],
    
    ```
],
```

## 使用

> 具体使用，请阅读 src/SendSms.php 文件

```
$result = Yii::$app->sms->send(
    'verificationCode',
    '13800138000',
    ['code' => '123456', 'product' => 'name']
);
if ($result['code'] == '0') {
    echo '发送成功';
} else {
    echo '发送失败: ' . $result['message'];
}
```