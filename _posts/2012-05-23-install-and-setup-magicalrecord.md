---
layout: post
title:  Install and setup MagicalRecord
Tags: iOS CoreData MagicalRecord
---
## install and setup

* 適当な場所にソースコードをclone

		git clone git://github.com/magicalpanda/MagicalRecord.git

* MagicalRecordフォルダを自分のプロジェクトへドラッグ
* プロジェクトの.pchファイルへ以下を記述

		#ifdef __OBJC__
			…
		    #define MR_SHORTHAND 1
		    #import "CoreData+MagicalRecord.h"
		#endif

	***MR_SHORTHAND**を**CoreData+MagicalRecord.h**のimportより前に記述すること*

* appDelegateに以下のどれか1つを記述

		+ (void) setupCoreDataStack;
		+ (void) setupAutoMigratingDefaultCoreDataStack;
		+ (void) setupCoreDataStackWithInMemoryStore;
		+ (void) setupCoreDataStackWithStoreNamed:(NSString *)storeName;
		+ (void) setupCoreDataStackWithAutoMigratingSqliteStoreNamed:(NSString *)storeName;

* 例（マイグレートに時間が掛かる場合はここに記述できない？）

		- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
		{
		    [MagicalRecord setupCoreDataStack];
		
		    return YES;
		}
		
		- (void)applicationWillTerminate:(UIApplication *)application
		{
		    [MagicalRecord cleanUp];
		}

* 参考

	[Using CoreData + MagicalRecord](http://ablfx.com/blog/2012/03/using-coredata-magicalrecord/)