---
layout: post
title: Cocos2d's Tips
Tags: Cocos2d
---
## 画面を縦向きにする

	- (BOOL)shouldAutorotateToInterfaceOrientation:(UIInterfaceOrientation)interfaceOrientation
	{
		return UIInterfaceOrientationIsLandscape(interfaceOrientation);
	}

`UIInterfaceOrientationIsLandscape`を`UIInterfaceOrientationIsPortrait`に変更

	return UIInterfaceOrientationIsPortrait(interfaceOrientation);

[How do I force portrait mode in Cocos2D?](http://stackoverflow.com/questions/10475309/how-do-i-force-portrait-mode-in-cocos2d)