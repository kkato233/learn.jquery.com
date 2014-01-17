---
title   : How jQuery Works
level: beginner
---

### jQuery: The Basics

This is a basic tutorial, designed to help you get started using jQuery. If you don't have a test page setup yet, start by creating the following HTML page:

これは基本的なチュートリアルです。
はじめて jQuery を開発する人向けの、
テストページをまだセットアップしていななら、
下記のHTMLページを作成してください。

```
<!doctype html>
<html>
<head>
	<meta charset="utf-8" />
	<title>Demo</title>
</head>
<body>
	<a href="http://jquery.com/">jQuery</a>
	<script src="jquery.js"></script>
	<script>

	// Your code goes here.

	</script>
</body>
</html>
```

The `src` attribute in the `<script>` element must point to a copy of jQuery. Download a copy of jQuery from the [Downloading jQuery](http://jquery.com/download/) page and store the `jquery.js` file in the same directory as your HTML file.

この `<script>` エレメントの中にある `src` 属性は jQuery のコピーを指す必要があります。
jQuery のサイト  [Downloading jQuery](http://jquery.com/download/) 
から コピーをダウンロードして `jquery.js` という名前で html ファイルと同じ場所に置きます。

### Launching Code on Document Ready
### Document Reay でコードを起動する。

To ensure that their code runs after the browser finishes loading the document, many JavaScript programmers wrap their code in an `onload` function:

確実にドキュメントを読み込んだあとで呼び出すために、
ブラウザがドキュメントを読み込んだ後で コードを実行させるため、
多くの JavaScript プログラマーは `onload` 関数で 囲んで呼び出します。

```
window.onload = function() {

	alert( "welcome" );

}
```

Unfortunately, the code doesn't run until all images are finished downloading, including banner ads. To run code as soon as the document is ready to be manipulated, jQuery has a statement known as the [ready event](http://api.jquery.com/ready/):

あいにくですが、このコードは すべての画像がダウンロード完了するまで 動作しません。
バナー広告の中にある画像なども・・。
できるだけ すぐに (as soon as) ドキュメントが ready になってから manipulated （操作する・扱う） するために
jQuery は  [ready event](http://api.jquery.com/ready/): というよく知られた 関数を持っています。

```

$( document ).ready(function() {

	// Your code here.

});
```

For example, inside the `ready` event, you can add a click handler to the link:

たとえば、 `ready` イベントの中で、
link のクリックハンドラを追加できる。


```
$( document ).ready(function() {

	$( "a" ).click(function( event ) {

		alert( "Thanks for visiting!" );

	});

});
```

Save your HTML file and reload the test page in your browser. Clicking the link should now first display an alert pop-up, then continue with the default behavior of navigating to http://jquery.com.

HTMLファイルを保存して リロードして、テストページをブラウザで開きます。
link をクリックすると 最初に 警告の Poupu が表示され、そして
最初の behavior of navigation の http://jquery.com を開きます。
最初に定義された である http://jquery.com を開きます。


For `click` and most other [events](http://api.jquery.com/category/events/), you can prevent the default behavior by calling `event.preventDefault()` in the event handler:

`click` や そのほかの  [events](http://api.jquery.com/category/events/) では、
デフォルトの振る舞い を イベントハンドラの中で  `event.preventDefault()`  を呼ぶことによって
 prevent (取り消す) 事が出来ます。


```
$( document ).ready(function() {

	$( "a" ).click(function( event ) {

		alert( "As you can see, the link no longer took you to jquery.com" );

		event.preventDefault();

	});

});
```

### Complete Example
### 完全な例

The following example illustrates the click handling code discussed above, embedded directly in the HTML `<body>`. Note that in practice, it is usually better to place your code in a separate JS file and load it on the page with a `<script>` element's `src` attribute.

次の例は クリックハンドラ の 上記の discussed したコードが
直接 HTML の `<body>` に埋め込まれている例です。
勉強のための 注意。
スクリプトファイルを別に作成して  `<script>` エレメントの `src` で ぺージに 読み込む方が よりベターです。

```
<!doctype html>
<html>
<head>
	<meta charset="utf-8" />
	<title>Demo</title>
</head>
<body>
	<a href="http://jquery.com/">jQuery</a>
	<script src="jquery.js"></script>
	<script>

	$( document ).ready(function() {
		$( "a" ).click(function( event ) {
			alert( "The link will no longer take you to jquery.com" );
			event.preventDefault();
		});
	});

	</script>
</body>
</html>
```

### Adding and Removing an HTML Class
### HTML クラスを 追加したり 削除したり

**Important:** *You must place the remaining jQuery examples inside the `ready` event so that your code executes when the document is ready to be worked on.*


**重要:** *You must place the remaining jQuery examples inside the `ready` event so that your code executes when the document is ready to be worked on.*

jQuery のコードは `ready` イベントの中に記入する必要があります。
そうしないと、ドキュメントが ready になってから実行されません。

Another common task is adding or removing a class.

First, add some style information into the `<head>` of the document, like this:

最初に いくつかの スタイルについての情報を ドキュメントの `<head>` に追加します。

このように：


```
<style>
a.test {
	font-weight: bold;
}
</style>
```

Next, add the [.addClass()](http://api.jquery.com/addClass/) call to the script:

次に  [.addClass()](http://api.jquery.com/addClass/)  呼び出しを追加します。

```
$( "a" ).addClass( "test" );
```

All `<a>` elements are now bold.

すべての `<a>` エレメントは 太字になりました。

To remove an existing class, use [.removeClass()](http://api.jquery.com/removeClass/):

クラスを削除するには  [.removeClass()](http://api.jquery.com/removeClass/) を使います。

```
$( "a" ).removeClass( "test" );
```

### Special Effects
### 特殊効果

jQuery also provides some handy [effects](http://api.jquery.com/category/effects/) to help you make your web sites stand out. For example, if you create a click handler of:

jQuery は いくつかの 簡単な  [effects](http://api.jquery.com/category/effects/) を提供しています。
たとえば、下記のようなクリックハンドラを作ったとすると：

```
$( "a" ).click(function( event ) {

	event.preventDefault();

	$( this ).hide( "slow" );

});
```

Then the link slowly disappears when clicked.

リンクをクリックすると リンクはゆっくり 消えていきます。


## Callbacks and Functions
## コールバックと関数

Unlike many other programming languages, JavaScript enables you to freely pass functions around to be executed at a later time. A *callback* is a function that is passed as an argument to another function and is executed after its parent function has completed. Callbacks are special because they patiently wait to execute until their parent finishes. Meanwhile, the browser can be executing other functions or doing all sorts of other work.

To use callbacks, it is important to know how to pass them into their parent function.

### Callback *without* Arguments
### パラメータの *ない* 関数

If a callback has no arguments, you can pass it in like this:

```
$.get( "myhtmlpage.html", myCallBack );
```

When [$.get()](http://api.jquery.com/jQuery.get/) finishes getting the page `myhtmlpage.html`, it executes the `myCallBack()` function.

* **Note:** The second parameter here is simply the function name (but *not* as a string, and without parentheses).

### Callback *with* Arguments

Executing callbacks with arguments can be tricky.

#### Wrong
This code example will ***not*** work:

```
$.get( "myhtmlpage.html", myCallBack( param1, param2 ) );
```

The reason this fails is that the code executes `myCallBack( param1, param2 )` immediately and then passes `myCallBack()`'s *return value* as the second parameter to `$.get()`. We actually want to pass the function `myCallBack()`, not `myCallBack( param1, param2 )`'s return value (which might or might not be a function). So, how to pass in `myCallBack()` *and* include its arguments?

#### Right

To defer executing `myCallBack()` with its parameters, you can use an anonymous function as a wrapper. Note the use of `function() {`. The anonymous function does exactly one thing: calls `myCallBack()`, with the values of `param1` and `param2`.

```
$.get( "myhtmlpage.html", function() {

	myCallBack( param1, param2 );

});
```

When `$.get()` finishes getting the page `myhtmlpage.html`, it executes the anonymous function, which executes `myCallBack( param1, param2 )`.
