# Taobao top SDK for laravel/lumen

### 安装
`composer require toptbk/toptbk`

### 配置
* 在config/app.php中的providers数组中添加`Wangma\TopClient\TopClientServiceProvider::class,`
* 在config/app.php中的aliases数组中添加`'TopClient' => Wangma\TopClient\Facades\TopClient::class,`
* 执行 `php artisan vendor:publish --provider="Wangma\TopClient\TopClientServiceProvider"` 生成配置文件
* 编辑.env文件，设置appid,appsecret


### 示例代码
```
php
use TopClient;
use TopClient\request\TbkItemGetRequest;

$topclient = TopClient::connection();
$req = new TbkItemGetRequest;
$req->setFields("num_iid,title,pict_url,reserve_price,zk_final_price,user_type,provcity,item_url");
$req->setQ('手机');
$req->setSort("tk_total_sales");
$req->setPageNo('1'); // 实验后发现必需用字符串的数字才能正确分页
$req->setPageSize('40');
$resp = $topclient->execute($req);
dd($resp);
```
