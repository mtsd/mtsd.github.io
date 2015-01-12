---
layout: post
Title: install and setup MySQL with Homebrew in OSX Lion
---
## LionにHomebrewでMySQLをインストールする

<hr />

**補足**


	$ brew install mysql
	...
	curl: (22) The requested URL returned error: 404
	Error: Download failed: http://downloads.mysql.com/archives/mysql-5.5/mysql-5.5.25.tar.gz

エラーが発生した時

	$ brew update

Homebrew自体をアップデートする

<hr />

{% gist matsuda/3186441 1_install_mysql.log %}

## setup MySQL

{% gist matsuda/3186441 2_setup_mysql_database.log %}


## 起動スクリプトの設定

	$ cp /usr/local/Cellar/mysql/5.5.25a/homebrew.mxcl.mysql.plist ~/Library/LaunchAgents/
	$ launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist


## 設定ファイル

	$ cp /usr/local/Cellar/mysql/5.5.25a/support-files/my-small.cnf /usr/local/var/mysql/my.cnf

## set password to root

	$ /usr/local/Cellar/mysql/5.5.25a/bin/mysqladmin -u root password 'new-password'

## 参考
* [HomebrewでMySQLをインストールする時に知っておきたいこと][1]

[1]: http://tukaikta.blog135.fc2.com/blog-entry-197.html
