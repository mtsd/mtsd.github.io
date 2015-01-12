---
layout: post
title:  Install and setup PostgreSQL with Homebrew
date:   2012-06-21 20:00:00
Tags: OSX Homebrew
---
## install PostgreSQL

	$ brew install postgresql

<script src="https://gist.github.com/2963485.js?file=1_install_postgresql.log"></script>

## 初期化

	$ initdb /usr/local/var/postgres

<script src="https://gist.github.com/2963485.js?file=2_create_postgresql_database.log"></script>

## PostgreSQLを起動

	$ pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log start

## PostgreSQLを終了

	$ pg_ctl -D /usr/local/var/postgres stop -s -m fast

## 参考

* [Mac に Homebrew で PostgreSQL をインストールする](http://codenote.net/ruby/187.html)