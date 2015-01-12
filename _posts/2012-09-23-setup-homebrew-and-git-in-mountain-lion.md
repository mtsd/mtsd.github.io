---
layout: post
title:  Setup Homebrew and git in Mountain Lion
Tags: Homebrew, git
---
**Mountain Lion** に **Homebrew** をインストールする。
また、その他開発ツールもインストールする。

## install Java

あらかじめ *java* をインストール

	$ java -version
	
で起動する画面からJavaをインストールする。

## install Homebrew

[Homebrew](http://mxcl.github.com/homebrew/)にある通り、以下のコマンドを実行。

	$ ruby <(curl -fsSkL raw.github.com/mxcl/homebrew/go)

Homebrewをインストールしたあとに、システムチェック?をする必要があるらしい。（以前は無かったと思うんだけど）

	$ brew doctor

Xcodeをインストールしてまだ一度も起動していない場合は、

	$ brew doctor
	Warning: You have not agreed to the Xcode license.
	Builds will fail! Agree to the license by opening Xcode.app or running:
    	xcodebuild -license

とエラーになるので、Xcodeを一度起動し、再度このコマンドを実行する。

	$ brew doctor
	Your system is raring to brew.

## install git

	$ brew install git

## initial git config

	$ git config --global user.name "your name"
	$ git config --global user.email "your email"

## setup git-completion

gitコマンドを補完する *git-completion* を設定。  
エイリアスで設定。

	$ ln -s /usr/local/etc/bash_completion.d/git-completion.bash ~/git-completion

## update Homebrew

gitをインストールできたら、Homebrew自体をアップデートする。

	$ brew update

## install readline

	$ brew install readline

これだけだとインストールされるだけで、/usr/localにシムリンクされていないので、

	$ brew link readline

## install other command tools

その他諸々のコマンドツールをインストール。

	$ brew install lv
	$ brew install wget

## インストールログ

[log of installing Homebrew](https://gist.github.com/3769845)
