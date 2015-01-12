---
layout: post
title:  Create rails project to deploy on Heroku
Tags: Rails rbenv Heroku
---
[macを買って、今すぐherokuでruby1.9.3 + rails3.2しよう！](http://ppworks.hatenablog.jp/entry/2012/03/04/141951)を参考

## rbenv-gemset

* rbenv-gemsetのインストール

		$ brew install rbenv-gemset
		==> Downloading https://github.com/jamis/rbenv-gemset/tarball/v0.3.0
		######################################################################## 100.0%
		/usr/local/Cellar/rbenv-gemset/0.3.0: 11 files, 48K, built in 2 seconds

* gemsetの作成

		$ rbenv gemset create 1.9.3-p125 mygemset

* activeなgemset

		$ rbenv gemset active 
		no active gemsets
		$ echo mygemset > .rbenv-gemsets
		$ rbenv gemset active 
		mygemset

## bundler

* bundlerのインストール

		$ rbenv exec gem install bundler
		Fetching: bundler-1.1.3.gem (100%)
		Successfully installed bundler-1.1.3
		1 gem installed
		Installing ri documentation for bundler-1.1.3...
		Installing RDoc documentation for bundler-1.1.3...
		$ rbenv rehash

## rails

* プロジェクトのdir作成

		$ mkdir sample
		$ cd sample

* Gemfile

		$ cat << EOS > Gemfile
		> source "http://rubygems.org"
		> gem "rails", "3.2.2"
		> EOS> > 

* railsのインストール

		$ bundle install --path vendor/bundle

* railsプロジェクトの作成

		$ bundle exec rails new .

## heroku

* 初期設定

		$ bundle exec heroku login
		$ bundle exec heroku keys:add

* setup

		$ bundle exec heroku apps:create --stack cedar
		$ bundel exec heroku labs:enable user_env_compile
		$ bundle exec heroku config:add RUBY_VERSION=ruby-1.9.3-p125

* deploy

		$ git init
		$ git add -A
		$ git commit -m 'create rails project'
		$ git push heroku master
