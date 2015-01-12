---
layout: post
title:  Setup twitter-bootstrap-rails
Tags: Rails Twitter-bootstrap
---
[前回]({% post_url 2012-05-06-create-rails-project-to-deploy-on-heroku %})の引き続きで`Twitter-bootstrap-rails`を試す  
また[こちらのブログ](http://ppworks.hatenablog.jp/entry/2012/02/19/033644)を参考にさせてもらう

## Twitter-bootstrap-railsのセットアップ

* `Gemfile`に`twitter-bootstrap-rails`を追加

		group :assets do
			...
			gem 'twitter-bootstrap-rails'
			...
		end

* インストール

		$ bundle install

* 追加されたgenerator

		$ bundle exec rails g -h
		...
		Bootstrap:
		  bootstrap:install
		  bootstrap:layout
		  bootstrap:themed
		...

* 初期設定

		$ bundle exec rails g bootstrap:install
		      insert  app/assets/javascripts/application.js
		      create  app/assets/javascripts/bootstrap.js.coffee
		      create  app/assets/stylesheets/bootstrap_and_overrides.css.less
		        gsub  app/assets/stylesheets/application.css
		        gsub  app/assets/stylesheets/application.css


## Railsのもろもろの設定

* controllerの作成

		$ bundle exec rails g controller Pages index

* `config/routes.rb`にroutingを設定

		  ...
		  root :to => 'pages#index'
		  ...

* `index.html`削除

		$ rm -f public/index.html

## Twitter-bootstrap-railsのlayout

* layout作成

		$ bundle exec rails g bootstrap:layout bootstrap fluid
		      create  app/views/layouts/bootstrap.html.erb

* layoutの変更  

	`app/views/layouts/bootstrap.html.erb`にlayoutを指定

		class ApplicationController < ActionController::Base
			layout 'bootstrap'
			protect_from_forgery
		end

* railsを起動

		$ bundle exec rails s
