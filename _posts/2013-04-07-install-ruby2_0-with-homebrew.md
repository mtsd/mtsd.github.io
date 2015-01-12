---
layout: post
title: Install Ruby 2.0 with Homebrew
Tags: Ruby rbenv ruby-build Homebrew  
---
以前にrbenvでRuby1.9.3環境を構築している（Xcode、Homebrew、rbenvなどインストール済み）状態でRuby2.0をインストールする

参考

* [OS X で rbenv を使って ruby 1.9.3 or 2.0.0 の環境を作る](http://qiita.com/items/9dd797f42e7bea674705)

## install openssl

	$ brew install openssl

## install Ruby 2.0

	$ RUBY_CONFIGURE_OPTS="--enable-shared --with-readline-dir=$(brew --prefix readline) --with-openssl-dir=$(brew --prefix openssl)"  rbenv install 2.0.0-p0

installされたか確認

	$ rbenv versions 
	* system (set by /Users/matsuda/.rbenv/version)
	  2.0.0-p0
	$ rbenv global 2.0.0-p0
	$ ruby -v
	ruby 2.0.0p0 (2013-02-24 revision 39474) [x86_64-darwin12.3.0]
	$ rbenv rehash

**追記(2013/04/22)**

## rbenvやruby-buildが古くてRuby2.0をインストールできない場合


ruby2.0をrbenvでインストールしようと思ったら、ruby-buildにruby2.0が無いというエラーになったための対処法

	$ RUBY_CONFIGURE_OPTS="--enable-shared --with-readline-dir=$(brew --prefix readline) --with-openssl-dir=$(brew --prefix openssl)"  rbenv install 2.0.0-p0
	ruby-build: definition not found: 2.0.0-p0


### Homebrewを最新にする

	$ brew update

### rbenvとruby-buildを最新にする

	$ brew upgrade rbenv
	$ brew upgrade ruby-build

**追記終わり(2013/04/22)**

## インストールログ

[install Ruby 2.0 with Homebrew](https://gist.github.com/matsuda/5329935)
