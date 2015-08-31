---
layout: post
tags: [Homebrew, Ruby, rbenv]
---

## install rbenv-gemset

~~~
$ brew install rbenv-gemset
$ rbenv gemset create 2.2.1 default
$ rbenv gemset list
$ rbenv gemset active
no active gemsets
~~~

## create gemset

~~~
$ rbenv gemset create 2.2.1 default
created default for 2.2.1
$ rbenv gemset list
2.2.1:
  default
$ rbenv gemset active
no active gemsets
~~~

## management gems for project

~~~
$ rbenv gemset init sample
created sample for 2.2.1
created and initialized the following gemset for use with 2.2.1
=====
sample
=====
$ cat .rbenv-gemsets
sample
$ rbenv gemset list
2.2.1:
  sample
  default
$ rbenv gemset active
sample global
~~~

## install gems

~~~
$ bundle init
Writing new Gemfile to /Users/xxx/sample/Gemfile
$ gem search ^cocoapods$ -a

*** REMOTE GEMS ***

cocoapods (0.36.2, 0.36.1, ...)

$ edit Gemfile # ex.emacs
$ cat Gemfile
# A sample Gemfile
source "https://rubygems.org"

gem 'cocoapods', '0.33.1'
$ bundle install --path vendor/bundle
~~~

## local

~~~
$ echo '.gems' > .rbenv-gemsets
$ gem install bundler
$ rbenv exec bundle install
~~~

## Appendix

* [rbenv-gemset](https://github.com/jf/rbenv-gemset)
* [rbenvを使ったRuby開発環境の構築](http://memo.saitodev.com/home/ruby/rbenv/)
