---
layout: post
title: ReactiveCocoaをSwift2で試す
tags: [iOS, Swift, ReactiveCocoa, Carthage]
---


[ReactiveCocoa](https://github.com/ReactiveCocoa/ReactiveCocoa)のSwift2.0対応を試す

## ReactiveCocoaのインストール

[Carthage](https://github.com/Carthage/Carthage)でインストールする  

* [以前試したCarthageの記事](/2015/08/31/Carthage.html)も参照

~~~
$ touch Cartfile
$ edit Cartfile
github "ReactiveCocoa/ReactiveCocoa" "swift2"

~~~

~~~
$ carthage update
*** Fetching ReactiveCocoa
*** Fetching Result
*** Checking out Result at "0.6-beta.1"
*** Checking out ReactiveCocoa at "5cb359c2ac17625ae9f4ce3ac955cc100d666fa6"
*** xcodebuild output can be found in /var/folders/gh/k78xg2h16t1g9hf6j5b6x71h0000gn/T/carthage-xcodebuild.Gnllh5.log
*** Building scheme "Result-iOS" in Result.xcodeproj
** BUILD FAILED **


The following build commands failed:
        CompileSwift normal x86_64 /Users/matsuda/Dev/iOS/Swift/TestReactiveCocoa/Carthage/Checkouts/Result/Result/ResultType.swift
        CompileSwift normal x86_64 /Users/matsuda/Dev/iOS/Swift/TestReactiveCocoa/Carthage/Checkouts/Result/Result/Result.swift
        CompileSwiftSources normal x86_64 com.apple.xcode.tools.swift.compiler
(3 failures)
/Users/matsuda/Dev/iOS/Swift/TestReactiveCocoa/Carthage/Checkouts/Result/Result/ResultType.swift:17:29: warning: 'ifSuccess ifSuccess' can be expressed more succinctly as '#ifSuccess'
/Users/matsuda/Dev/iOS/Swift/TestReactiveCocoa/Carthage/Checkouts/Result/Result/Result.swift:26:35: error: expected ',' separator
/Users/matsuda/Dev/iOS/Swift/TestReactiveCocoa/Carthage/Checkouts/Result/Result/Result.swift:28:24: error: expected ',' separator
~~~

こんなエラーが出たら `xcode-select` でXcode-betaを利用するように変更する。

* [CarthageでReactiveCocoaのSwift 2.0版を導入する](http://qiita.com/masahikot/items/8b42e2679608bf785454)

~~~
$ sudo xcode-select --switch /Applications/Xcode-beta.app
$ carthage update
*** Fetching ReactiveCocoa
*** Fetching Result
*** Checking out Result at "0.6-beta.1"
*** Checking out ReactiveCocoa at "5cb359c2ac17625ae9f4ce3ac955cc100d666fa6"
*** xcodebuild output can be found in /var/folders/gh/k78xg2h16t1g9hf6j5b6x71h0000gn/T/carthage-xcodebuild.Mqd3tc.log
*** Building scheme "Result-Mac" in Result.xcodeproj
*** Building scheme "Result-watchOS" in Result.xcodeproj
*** Building scheme "Result-iOS" in Result.xcodeproj
*** Building scheme "ReactiveCocoa Mac" in ReactiveCocoa.xcworkspace
*** Building scheme "ReactiveCocoa-watchOS" in ReactiveCocoa.xcworkspace
*** Building scheme "ReactiveCocoa iOS" in ReactiveCocoa.xcworkspace
~~~

## ReactiveCocoaの実装

下記の記事を参考に、"ReactiveCocoa Tutorial - RAYWENDERLICH"のコードを`Swift2.0`で書きなおしてみた。

[TestReactiveCocoa](https://github.com/matsuda/SwiftSamples/tree/master/TestReactiveCocoa)


### 参照

* [ReactiveCocoa Tutorial – The Definitive Introduction: Part 1/2](http://www.raywenderlich.com/62699/reactivecocoa-tutorial-pt1)
* [ReactiveCocoa Tutorial – The Definitive Introduction: Part 2/2](http://www.raywenderlich.com/62796/reactivecocoa-tutorial-pt2)
* [[swift] swiftでReactiveCocoa](http://www.kuma-de.com/blog/2015-01-10/6872)