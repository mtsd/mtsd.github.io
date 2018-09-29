# Install Jenkins to macOS High Sierra



```
$ brew install jenkins
jenkins: Java 1.8 is required to install this formula.
JavaRequirement unsatisfied!
You can install with Homebrew Cask:
 brew cask install homebrew/cask-versions/java8
You can download from:
 https://www.oracle.com/technetwork/java/javase/downloads/index.html
Error: An unsatisfied requirement failed this build.
```

## Java(8)

```
$ brew cask install homebrew/cask-versions/java8
==> Tapping homebrew/cask
Cloning into '/usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask'...
remote: Counting objects: 4148, done.
remote: Compressing objects: 100% (4129/4129), done.
remote: Total 4148 (delta 26), reused 759 (delta 16), pack-reused 0
Receiving objects: 100% (4148/4148), 1.30 MiB | 327.00 KiB/s, done.
Resolving deltas: 100% (26/26), done.
Tapped 1 command and 4050 casks (4,157 files, 4.1MB).
==> Tapping homebrew/cask-versions
Cloning into '/usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask-versions'...
remote: Counting objects: 215, done.
remote: Compressing objects: 100% (211/211), done.
remote: Total 215 (delta 17), reused 40 (delta 3), pack-reused 0
Receiving objects: 100% (215/215), 85.53 KiB | 9.50 MiB/s, done.
Resolving deltas: 100% (17/17), done.
Tapped 195 casks (234 files, 322KB).
==> Caveats
This Cask makes minor modifications to the JRE to prevent issues with
packaged applications, as discussed here:

  https://bugs.eclipse.org/bugs/show_bug.cgi?id=411361

If your Java application still asks for JRE installation, you might need
to reboot or logout/login.

Installing java8 means you have AGREED to the license at
  https://www.oracle.com/technetwork/java/javase/terms/license/index.html

==> Satisfying dependencies
==> Downloading http://download.oracle.com/otn-pub/java/jdk/8u181-b13/96a7b8442fe848ef90c96a2fad6ed6d1/jdk-8u181-macosx-x64.dmg
==> Downloading from http://download.oracle.com/otn-pub/java/jdk/8u181-b13/96a7b8442fe848ef90c96a2fad6ed6d1/jdk-8u181-macosx-x64.dmg?AuthPar
######################################################################## 100.0%
==> Verifying SHA-256 checksum for Cask 'java8'.
==> Installing Cask java8
==> Creating Caskroom at /usr/local/Caskroom
==> We'll set permissions properly so we won't need sudo in the future.
Password:
==> Running installer for java8; your password may be necessary.
==> Package installers may write to any location; options such as --appdir are ignored.
installer: Package name is JDK 8 Update 181
installer: Installing at base path /
installer: The install was successful.
🍺  java8 was successfully installed!
```

## Jenkins

```
$ brew install jenkins
Updating Homebrew...
==> Auto-updated Homebrew!
Updated 1 tap (homebrew/core).
==> Updated Formulae
codequery

==> Downloading http://mirrors.jenkins.io/war/2.141/jenkins.war
==> Downloading from http://ftp.yz.yamagata-u.ac.jp/pub/misc/jenkins/war/2.141/jenkins.war
######################################################################## 100.0%
==> jar xvf jenkins.war
==> Caveats
Note: When using launchctl the port will be 8080.

To have launchd start jenkins now and restart at login:
  brew services start jenkins
Or, if you don't want/need a background service you can just run:
  jenkins
==> Summary
🍺  /usr/local/Cellar/jenkins/2.141: 7 files, 75.4MB, built in 44 seconds
```

## boot Jenkins

```
$ jenkins
...

*************************************************************
*************************************************************
*************************************************************

Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

1a59475dc7a6483bb8e93e800654777e

This may also be found at: /Users/xxxxxx/.jenkins/secrets/initialAdminPassword

*************************************************************
*************************************************************
*************************************************************

...

```

http://localhost:8080 にアクセスし、表示されたGetting Started画面で上記のパスワードを入力する。  
次にプラグインのインストールとユーザー設定をして完了。
