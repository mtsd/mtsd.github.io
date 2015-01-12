---
layout: post
title: 開発開始および開発中でのCocoaPodsの利用について
tags: CocoaPods
---
## setup myself CocoaPods' spec repository

まず自分自身が個人で利用するspecファイルリポジトリを設定する。  
参考:[Private Pods](http://guides.cocoapods.org/making/private-cocoapods.html)  

例えば、githubにspec用のリポジトリを作成する。  
そしてローカルのCocoaPodsリポジトリに追加する。

	$ pod repo add mypods git@github.com:matsuda/CocoaPodsSpecs.git

## create new spec

CocoaPodsのマスターリポジトリに自分が利用しようと思っているライブラリのspecがない場合

例）Hogeライブラリ

1. specファイルを作成する。

		$ cd my-cocoapods-spec-dir # 自分のspecリポジトリのディレクトリ
		$ mkdir -p Hoge/0.0.1
		$ touch Hoge/0.0.1/Hoge.podspec
		$ edit

2. 作成したspecが正しく作成できているかインストールを試す。  
	specの参照先を1で作成したspecにする。

		$ cd my-project # 自分の開発プロジェクトのディレクトリ
		$ touch Podfile
		$ cat Podfile
		pod 'Hoge', :podspec => 'my-cocoapods-spec-dir/Hoge/0.0.1/Hoge.podspec'

		$ pod install
		Analyzing dependencies
		Fetching podspec for `Hoge` from `my-cocoapods-spec-dir/Hoge/0.0.1/Hoge.podspec`
		Downloading dependencies
		Installing Hoge (0.0.1)
		Generating Pods project
		Integrating client project

		[!] From now on use `my-project.xcworkspace`.

3. 自分のspecリポジトリに追加する。  
	自動で自分のリモートspecリポジトリにpushもしてくれる。

		$ pod push mypods Hoge/0.0.1/Hoge.podspec 
		
		Validating spec
		 -> Hoge (0.0.1)

		Updating the `mypods' repo

		Already up-to-date.

		Adding the spec to the `mypods' repo

		 - [Add] Hoge (0.0.1)

		Pushing the `mypods' repo

		To git@github.com:matsuda/CocoaPodsSpecs.git
		   13bfdff..d2c7427  master -> master

4. specの参照先が自分のspecリポジトリになるようにPodfileを編集し、再度インストールを試す。

		$ cat Podfile
		pod 'Hoge', '~> 0.0.1'

		$ pod install
		Analyzing dependencies
		Downloading dependencies
		Using Hoge (0.0.1)
		Generating Pods project
		Integrating client project
