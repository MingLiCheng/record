# JS 操作浏览器 Cookie

Cookie 是一段文本信息，伴随着用户请求在 web 和 server 之间进行传递。用户访问站点时，web 应用可以读取 Cookie 包含的信息。

> 项目使用 Cookie 对用户的登陆信息进行存储

```javascript
// 创建设置Cookie
setCookie(name, value, expiredays) {
	var exdate = new Date();
	exdate.setDate(exdate.getDate() + expiredays);
	var value = Base64.encode(value)
	document.cookie = name + "=" + escape(value) +
        ((expiredays == null) ? "" : ";path=/;expires=" + exdate.toGMTStrin())
},
// 获取 Cookie的信息
getCookie(name, base64) {
	var arr, reg = new RegExp("(^| )" + name + "=([^;]*)(;|$)");
	if (arr = document.cookie.match(reg)) {
		if (base64 === true)
			return Base64.decode(unescape(arr[2]));
		else
			return unescape(arr[2]);
	} else
		return null;
},
// 删除 Cookie的信息
delCookie(name) {
	var exp = new Date();
	exp.setTime(exp.getTime() - 1);
	var cval = this.getCookie(name, true);
	if (cval != null)
		document.cookie = name + "=" + cval + ";expires=" + exp.toGMTString();
}
```
