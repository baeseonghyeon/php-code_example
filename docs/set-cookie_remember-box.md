# set cookie, remember box (쿠키에 세션 넣기)

```php+HTML
<? if ($_COOKIE[login_id_remember]) {?>
	<input class="magic-checkbox" type="checkbox" name="remember" value="1" id="2" checked checked="checked">
<?} else {?>
	<input class="magic-checkbox" type="checkbox" name="remember" value="1" id="2">
<? } ?>
<!--value 1을 담은 체크박스를 통해 아이디 저장 체크 -->
```
```php
$remember = $_REQUEST[remember];	
//cookie, remember box
if ( $remember === '1' ) {
    setcookie('user_remember', $row[phone], time()+86400 * 365);
    setcookie('login_id_remember', $_REQUEST[login_id], time()+86400 * 365);
} else {
    setcookie('user_remember', "", time()-3600);
    setcookie('login_id_remember', "", time()-3600);
}
//체크박스의 벨류가 1일때 user의 phone data를 쿠키에 담음, 1년 동안 유지되는쿠키, 1이 아닐때 쿠키를 제거
```
```php
<?php
session_start();
if($_SESSION[phone] == NULL){
	if($_COOKIE[user_remember]) {
		$_SESSION[phone] = $_COOKIE[user_remember];
	}
	else {
	}
}
?>
//세션 폰이 null 일때 쿠키(폰 데이터)가 존재한다면 세션 폰에 쿠키를 넣어줌
```
