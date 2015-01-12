---
layout: post
title: Setup tmux with Homebrew
Tags: Homebrew, tmux 
---
## install tmux

	$ brew install tmux

{% gist matsuda/4523629 1_install_tmux.log %}

## Macでクリップボードを利用する

以下を参考

[Macのtmuxでクリップボードを使用、あとtmuxの自動起動とか](http://yonchu.hatenablog.com/entry/20120514/1337026014)

	$ brew install reattach-to-user-namespace

{% gist matsuda/4523629 2_install_reattach-to-user-namespace.log %}

	$ emacs /usr/local/bin/tmuxx
	$ chmod +x /usr/local/bin/tmuxx
	$ emacs /usr/local/bin/tmux-pbcopy
	$ chmod +x /usr/local/bin/tmux-pbcopy
