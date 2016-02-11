---
layout: post
title: setup Apache on El Capitan
tags: OSX
---

`El Capitan`に標準でインストールされている`Apache`について調べる

	$ httpd -v
	Server version: Apache/2.4.16 (Unix)
	Server built:   Jul 31 2015 15:53:26

## 起動と停止

* 起動

		$ sudo apachectl start

	[http://localhost](http://localhost)にアクセスして**It works!**と表示されることを確認  
	これは`/Library/WebServer/Documents`ディレクトリ配下の内容が表示される

* 停止

		$ sudo apachectl stop

* 自動起動させる設定

		$ sudo launchctl load -w /System/Library/LaunchDaemons/org.apache.httpd.plist

## 設定

[http://localhost](http://localhost)の表示対象の`/Library/WebServer/Documents`配下はシステムで共通で利用されるので、
ユーザ毎に利用するユーザディレクトリを利用できるように設定する。  
`Apache`の各種設定ファイルは`/etc/apache2`ディレクトリ配下にある  

### `httpd.conf`の編集

`/etc/apache2/httpd.conf`を編集する

	#LoadModule userdir_module libexec/apache2/mod_userdir.so
	↓
	LoadModule userdir_module libexec/apache2/mod_userdir.so

	#Include /private/etc/apache2/extra/httpd-userdir.conf
	↓
	Include /private/etc/apache2/extra/httpd-userdir.conf


### `httpd-userdir.conf`の編集
`/etc/apache2/extra/httpd-userdir.conf`を編集する

	#Include /private/etc/apache2/users/*.conf
	↓
	Include /private/etc/apache2/users/*.conf

`/etc/apache2/users`ディレクトリ配下に自分のユーザディレクトリ用の設定ファイルを作成する。  
なお、`/etc/apache2/users`ディレクトリ配下に参考となる`Guest.conf`というファイルがあるのでコピー

	$ sudo cp /etc/apache2/users/Guest.conf /etc/apache2/users/{ユーザ名}.conf

### `{ユーザ名}.conf`の編集

	<Directory "/Users/{ユーザ名}/Sites/">
        Options Indexes MultiViews
        Options +FollowSymLinks
        AllowOverride All
        Require all granted
	</Directory>

### 動作確認

設定ファイルの変更をチェックしてリスタート

	$ apachectl configtest
	$ sudo apachectl restart

### index.htmlの作成

ユーザディレクトリを作成

	$ mkdir ~/Sites

`~/Sites`ディレクトリ配下に適当に`index.html`を作成

[http://localhost/~{ユーザ名}/](http://localhost/~{ユーザ名}/)にアクセスして、
今作成した`index.html`が表示されることを確認

## 参考

* [http://nantekottai.com/2014/10/26/os-x-10-10-sites/](http://nantekottai.com/2014/10/26/os-x-10-10-sites/)