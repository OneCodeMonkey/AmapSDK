# AmapSDK
AMap SDK for PHP (高德地图 web API) 

基础 HTTP 请求使用协程版 guzzle http，所以支持在 swoole 协程环境下使用。

安装
```bash
composer require onecodemonkey/amap_sdk 
```
使用
```php
<?php

use Amap\Amap;
use Hyperf\Guzzle\ClientFactory;
use Hyperf\Di\Annotation\Inject;

class Test {
    /**
     * @Inject
     * @var ClientFactory
     */
    private $clientFactory;
    
    /**
     * 搜索周边 POI
     */
    public function testSearchAround()
    {
        $options = [
            'key' => 'XXX',
        ];
        $client = new Amap($options, $this->clientFactory);
        
        $params = [
            'types' => 150500,  // 地铁站
            "offset" => 25,
            "page" => 1,
        ];
        
        $result = $client->aroundSearch("116.740000,40.330000", $params);
        
        var_dump($result);
    }
}
```
