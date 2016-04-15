# social-login
第三方登录聚合包
* [QQ第三方登录(网页应用 OAuth2.0 自适配WAP网站)](#QQ第三方登录)
* 微信第三方登录(网页应用PC版:即扫码登录)(开发中...)

### composer安装包

```php
// todo
```

### QQ第三方登录

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
$qq->appId = '100481313';
$qq->appKey = '06663346dc50543d42108206afdc1313';
$qq->redirectUri = 'http://www.example.com/qq/callback.php';

try {
    $userInfo = $qq->getUserInfo();
} catch (Exception $e) {
    $userInfo = [];
    var_dump($e->getMessage());
}
var_dump($userInfo);
```

## License

MIT