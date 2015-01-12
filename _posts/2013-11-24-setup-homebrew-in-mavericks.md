---
layout: post
tags: Homebrew
---
以前にMountain LionでHomebrewを設定する方法をメモしたが、今回は **Marvericks** に **Homebrew** を設定する。

## install Homebrew

以前必要だった *java* のインストール作業は必要なかった。

[Homebrew](http://brew.sh) を参考に

	$ ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go/install)"

	$ brew doctor

一度もXcodeを起動したことがないとエラーになるので、その場合はXcodeを一度起動して、再度コマンドを実行する。

## install and setup git

### install git

	$ brew install git

### initial git config

	$ git config --global user.name "your name"
	$ git config --global user.email "your email"

## update Homebrew

gitをインストールできたら、Homebrew自体をアップデートする。

	$ brew update

## install command tools

### install readline

	$ brew install readline

### install others

その他諸々のコマンドツールをインストール。

	$ brew install lv
	$ brew install wget
	$ brew install openssl

## setup for github

[Generating SSH Keys](https://help.github.com/articles/generating-ssh-keys)のとおりに公開鍵認証のためのSSHキーを生成する。

### set SSH keys

	$ ssh-keygen -t rsa -C "email"

## setup dotfiles

各dot系のファイルの設定

自分の[dotfilesリポジトリ](https://github.com/matsuda/dotfiles)からクローン

	$ mkdir -p dev/github && cd dev/github # 適当なディレクトリを作って
	$ git clone git@github.com:matsuda/dotfiles.git

各dotファイルにエイリアスを設定

	$ ln -s dev/github/dotfiles/dot.bashrc ~/.bashrc
	$ ln -s dev/github/dotfiles/dot.bash_profile ~/.bash_profile
	$ ln -s dev/github/dotfiles/dot.inputrc ~/.inputrc
	$ ln -s dev/github/dotfiles/dot.gitignore ~/.gitignore
	$ ln -s dev/github/dotfiles/dot.screenrc ~/.screenrc
	$ ln -s dev/github/dotfiles/dot.lv ~/.lvrc
	$ ln -s dev/github/dotfiles/dot.sqliterc ~/.sqliterc

カスタマイズが必要そうなdotファイルはコピー

	$ cp dev/github/dotfiles/dot.gitconfig .gitconfig
	$ cp dev/github/dotfiles/dot.bash_local .bash_local

ロードする

	$ source ~/.bash_profile
	$ source ~/.bashrc

## インストールログ

[log of setup Homebrew and install development tools in Marvericks](https://gist.github.com/matsuda/7623322)