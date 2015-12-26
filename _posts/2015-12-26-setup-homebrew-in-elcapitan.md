---
layout: post
title: Setup Homebrew In El Capitan
tags: Homebrew
---

* [Mavericks版](/2013/11/24/setup-homebrew-in-mavericks.html)の修正

## install Homebrew

[Homebrew](http://brew.sh) を参考に

	$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
	$ brew doctor
	$ brew update

## install command tools

	$ brew install git lv wget
	(openssl)
	$ brew install readline

(readlineは[setup rbenv 2015年度](/2015/12/27/setup-rbenv-in-2015.html)でインストールしてもよい)

### setup git config

	$ git config --global user.name "your name"
	$ git config --global user.email "your email"

## setup for github

[Generating SSH Keys](https://help.github.com/articles/generating-ssh-keys)のとおりに公開鍵認証のためのSSHキーを生成する。

### set SSH keys

	$ ssh-keygen -t rsa -b 4096 -C "email"

## setup dotfiles

各dot系のファイルの設定

自分の[dotfilesリポジトリ](https://github.com/matsuda/dotfiles)からクローン

	$ mkdir -p Dev/github && cd Dev/github # 適当なディレクトリを作って
	$ git clone git@github.com:matsuda/dotfiles.git

各dotファイルにエイリアスを設定

	$ ln -s Dev/github/dotfiles/dot.bashrc ~/.bashrc
	$ ln -s Dev/github/dotfiles/dot.bash_profile ~/.bash_profile
	$ ln -s Dev/github/dotfiles/dot.inputrc ~/.inputrc
	$ ln -s Dev/github/dotfiles/dot.gitignore ~/.gitignore
	$ ln -s Dev/github/dotfiles/dot.screenrc ~/.screenrc
	$ ln -s Dev/github/dotfiles/dot.lv ~/.lvrc
	$ ln -s Dev/github/dotfiles/dot.sqliterc ~/.sqliterc

カスタマイズが必要そうなdotファイルはコピー

	$ cp Dev/github/dotfiles/dot.gitconfig .gitconfig
	$ cp Dev/github/dotfiles/dot.bash_local .bash_local

ロードする

	$ source ~/.bash_profile
	$ source ~/.bashrc
