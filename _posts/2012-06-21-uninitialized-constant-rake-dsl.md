---
layout: post
title:  uninitialized constant Rake::DSL
date:   2012-06-21 22:00:00
Tags: Ruby
---
	uninitialized constant Rake::DSL

というエラーが出た時の対処

Gemfileに

	source 'http://rubygems.org'
	source 'http://gems.github.com'

	gem 'rake', '0.8.7'

	…

を追加してbundleをアップデート

	$ bundle 
	Fetching source index for http://rubygems.org/
	Fetching source index for http://gems.github.com/
	You have requested:
	  rake = 0.8.7

	The bundle currently has rake locked at 0.9.2.2.
	Try running `bundle update rake`

というエラーが出るので

	$ bundle update rake

を実行