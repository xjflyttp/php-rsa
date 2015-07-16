php-rsa
========

composer.json
-----
```json
"require": {
    "xj/php-rsa": "*"
},
```

Rsa
----
```
openssl genrsa -out rsa_private_key.pem 2048
openssl rsa -in rsa_private_key.pem -pubout -out rsa_public_key.pem
```

example:
-----
```php
use xj\phprsa\RsaPrivate;
use xj\phprsa\RsaPublic;

//init
$privateKey = '/common/config/key-private.php';
$publicKey = '/common/config/key-public.php';
$str = 'php-rsa';

//private encrypt -> public decrypt
$privateEncryptString = RsaPrivate::model($privateKey)->encrypt($str);
$publicDecryptString = RsaPublic::model($publicKey)->decrypt($privateEncryptString);
var_dump('private', $str, $privateEncryptString, $publicDecryptString);

//public encrypt -> private decrypt
$publicEncryptString = RsaPublic::model($publicKey)->encrypt($str);
$privateDecryptString = RsaPrivate::model($privateKey)->decrypt($publicEncryptString);
var_dump('public', $str, $publicEncryptString, $privateDecryptString);
```
