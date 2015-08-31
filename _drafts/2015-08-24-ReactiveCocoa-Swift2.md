---
layout: post
title: ReactiveCocoaをSwift2で試す
tags: [iOS, Swift, ReactiveCocoa]
---

# ReactiveCocoa

Swift2.0対応を試す

## Carthage

* [iOS 7 でも Carthage を使おう](http://qiita.com/koher/items/a3b254d0195669088e40)

~~~
$ brew update
$ brew install carthage
($ brew upgrade carthage)
~~~

## Xcode

* [CarthageでSwift 1.2に対応したライブラリをビルド](http://blog.ishkawa.org/2015/03/06/1425625466/)

~~~
$ sudo xcode-select --switch /Applications/Xcode-beta.app
$ xcode-select --print-path
/Applications/Xcode-beta.app/Contents/Developer
~~~

## ReactiveCocoa

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
