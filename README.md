# social-login
第三方登录聚合包
* QQ第三方登录(网页应用 OAuth2.0 自适配WAP网站)
* 微信第三方登录(网页应用PC版:即扫码登录)(开发中...)

#### composer安装包

```php
composer require gaoming13/social-login
```

#### QQ第三方登录

- 获取跳转至登录页面的链接

```php
use \Gaoming13\SocialLogin\Qq;

$qq = new Qq();
$qq->appId = '100481313';
$qq->appkey = '06663346dc50543d42108206afdc1313';
$qq->redirectUri = 'http://www.example.com/qq/callback.php';

$loginUrl = $qq->getLoginUrl();

header('Location: ' . $loginUrl);
```

- 回调页面获取用户信息

```php
use Gaoming13\SocialLogin\Qq;

$qq = new Qq();

$qq->appId = '100482626';
$qq->appKey = '06663346dc50543d42108206afdc7539';
$qq->redirectUri = 'http://www.bcsh.com/qq/callback.php';

try {
    $uid = $qq->getUid();
    $userInfo = $qq->getUserInfo();

    var_dump($uid);
    var_dump($userInfo);
} catch (Exception $e) {
    var_dump($e->getMessage());
}
```

- 响应数据
```
array (size=18)
  'ret' => int 0
  'msg' => string '' (length=0)
  'is_lost' => int 0
  'nickname' => string '高明' (length=6)
  'gender' => string '男' (length=3)
  'province' => string '上海' (length=6)
  'city' => string '浦东新区' (length=12)
  'year' => string '1990' (length=4)
  'figureurl' => string 'http://qzapp.qlogo.cn/qzapp/100482626/A51D821DB5103503471A4D3951D4F906/30' (length=73)
  'figureurl_1' => string 'http://qzapp.qlogo.cn/qzapp/100482626/A51D821DB5103503471A4D3951D4F906/50' (length=73)
  'figureurl_2' => string 'http://qzapp.qlogo.cn/qzapp/100482626/A51D821DB5103503471A4D3951D4F906/100' (length=74)
  'figureurl_qq_1' => string 'http://q.qlogo.cn/qqapp/100482626/A51D821DB5103503471A4D3951D4F906/40' (length=69)
  'figureurl_qq_2' => string 'http://q.qlogo.cn/qqapp/100482626/A51D821DB5103503471A4D3951D4F906/100' (length=70)
  'is_yellow_vip' => string '0' (length=1)
  'vip' => string '0' (length=1)
  'yellow_vip_level' => string '0' (length=1)
  'level' => string '0' (length=1)
  'is_yellow_year_vip' => string '0' (length=1)
```

## License

MIT