---
layout: post
title: Setup rbenv and ruby-build
Tags: Ruby rbenv ruby-build Homebrew
---
## install rbenv

	$ brew install rbenv

## install ruby-build

	$ brew install ruby-build

## init rbenv to profile

rbenvの初期化処理をprofileに追加 (2013/04/07)

	# ~/.bash_profile
	...
	if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
	...

2013/04/07以前はこうしていたが、上記の設定をすれば不要

	$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
	$ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile

## ~~rbenvコマンドの補完ツールの設定~~

上記のrbenv初期化設定をすればこれは不要 (2013/04/07)  

~~Homebrewでrbenvをインストールした場合、Celler配下にコマンドツールがあるので、ホーム直下にシンボリックリンクを作成し、profileに設定する~~

	$ mkdir .rbenv/completions && ln -s /usr/local/Cellar/rbenv/0.3.0/completions/rbenv.bash .rbenv/completions/rbenv.bash
	$ echo 'source ~/.rbenv/completions/rbenv.bash' >> ~/.bash_profile
	
## install Ruby (1.9.2-p320)

### Rubyをインストール

	$ CONFIGURE_OPTS="--with-readline-dir=/usr/local" rbenv install 1.9.2-p320

rbenvでRubyをインストールしようとするとエラーが発生

ruby-1.9.3-p125より古いrubyをビルドするためには、Appleの提供するllvm-gccではない公式GCCコンパイラが必要とのこと

{% gist matsuda/3930039 3_install_ruby_but_error %}

### install GCC compiler

[kennethreitz / osx-gcc-installer](https://github.com/kennethreitz/osx-gcc-installer) からGCCコンパイラをダウンロードしてインストールする

### 再度Rubyのインストールを試す

	$ CONFIGURE_OPTS="--with-readline-dir=/usr/local" rbenv install 1.9.2-p320

## デフォルトで利用するRubyのバージョンを設定

	$ ruby -v
	ruby 1.8.7 (2012-02-08 patchlevel 358) [universal-darwin12.0]

	$ rbenv global 1.9.2-p320

	$ ruby -v
	ruby 1.9.2p320 (2012-04-20 revision 35421) [x86_64-darwin12.2.0]

## rehash

	$ rbenv rehash

## インストールログ

[log of installing rbenv and ruby-build](https://gist.github.com/3930039)
