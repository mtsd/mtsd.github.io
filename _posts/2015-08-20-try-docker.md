---
layout: post
title: Docker
tags: [Docker]
---

## Dockerのセットアップ

* [MacでDockerを試してみる](http://qiita.com/itopan88/items/8be49baae40df392f6f2)

この記事をそのまんま試してみる

### Dockerのインストール

~~~
$ brew update
$ brew --version
0.9.5
$ brew tap homebrew/binary
$ brew install docker boot2docker
==> Downloading https://homebrew.bintray.com/bottles/docker-1.8.1.yosemite.bottle.tar.gz
######################################################################## 100.0%
==> Pouring docker-1.8.1.yosemite.bottle.tar.gz
==> Caveats
Bash completion has been installed to:
  /usr/local/etc/bash_completion.d

zsh completion has been installed to:
  /usr/local/share/zsh/site-functions
==> Summary
🍺  /usr/local/Cellar/docker/1.8.1: 9 files, 8.9M
==> Downloading https://homebrew.bintray.com/bottles/boot2docker-1.8.0.yosemite.bottle.tar.gz
######################################################################## 100.0%
==> Pouring boot2docker-1.8.0.yosemite.bottle.tar.gz
==> Caveats
Rebuild the VM after an upgrade with:
  boot2docker destroy && boot2docker upgrade

To have launchd start boot2docker at login:
  ln -sfv /usr/local/opt/boot2docker/*.plist ~/Library/LaunchAgents
Then to load boot2docker now:
  launchctl load ~/Library/LaunchAgents/homebrew.mxcl.boot2docker.plist
==> Summary
🍺  /usr/local/Cellar/boot2docker/1.8.0: 3 files, 7.3M
~~~

~~~
$ docker -v
Docker version 1.8.1, build d12ea79
$ boot2docker 
Usage: boot2docker [<options>] {help|init|up|ssh|save|down|poweroff|reset|restart|config|status|info|ip|shellinit|delete|download|upgrade|version} [<args>]
~~~

### ISO(仮想)マシンイメージをダウンロード

~~~
$ boot2docker init

  WARNING: The 'boot2docker' command line interface is officially deprecated.

  Please switch to Docker Machine (https://docs.docker.com/machine/) ASAP.

  Docker Toolbox (https://docker.com/toolbox) is the recommended install method.

Latest release for github.com/boot2docker/boot2docker is v1.8.1
Downloading boot2docker ISO image...
Success: downloaded https://github.com/boot2docker/boot2docker/releases/download/v1.8.1/boot2docker.iso
	to /Users/matsuda/.boot2docker/boot2docker.iso
Generating public/private rsa key pair.
Your identification has been saved in /Users/matsuda/.ssh/id_boot2docker.
Your public key has been saved in /Users/matsuda/.ssh/id_boot2docker.pub.
The key fingerprint is:

===< snip >===

Initialization of virtual machine "boot2docker-vm" complete.
Use `boot2docker up` to start it.
~~~

### 仮想マシンを起動

~~~
$ boot2docker up

  WARNING: The 'boot2docker' command line interface is officially deprecated.

  Please switch to Docker Machine (https://docs.docker.com/machine/) ASAP.

  Docker Toolbox (https://docker.com/toolbox) is the recommended install method.

Waiting for VM and Docker daemon to start...
......................ooooooooooo
Started.
Writing /Users/matsuda/.boot2docker/certs/boot2docker-vm/ca.pem
Writing /Users/matsuda/.boot2docker/certs/boot2docker-vm/cert.pem
Writing /Users/matsuda/.boot2docker/certs/boot2docker-vm/key.pem

To connect the Docker client to the Docker daemon, please set:
    export DOCKER_HOST=tcp://192.168.59.103:2376
    export DOCKER_CERT_PATH=/Users/matsuda/.boot2docker/certs/boot2docker-vm
    export DOCKER_TLS_VERIFY=1

Or run: `eval "$(boot2docker shellinit)"`
~~~

~~~
$ boot2docker status
running
~~~

`.bash_profile`に上記の設定（export ...）を追記する

### イメージファイルを落とす

~~~
$ docker pull centos:latest
latest: Pulling from library/centos
f1b10cd84249: Pull complete 
c852f6d61e65: Pull complete 
7322fbe74aa5: Pull complete 
Digest: sha256:90305c9112250c7e3746425477f1c4ef112b03b4abe78c612e092037bfecc3b7
Status: Downloaded newer image for centos:latest
~~~

### コンテナの起動

~~~
[matsuda@1020409 ~:]$ docker run -t -i centos /bin/bash
[root@d321c8c05977 /]#
~~~

~~~
$ docker run -t -i -d centos /bin/bash
98d99c50c39e4aa0f123305b0784fbdf7575449dead63b76ecb447e043b8a03e
$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
98d99c50c39e        centos              "/bin/bash"         11 seconds ago      Up 11 seconds                           admiring_archimedes
~~~

Status列が「Up」になっていると実行中

### コンテナの停止

~~~
$ docker stop 98d99c50c39e
~~~

### CentOS6のイメージファイルを落とす

~~~
$ docker pull centos:centos6
centos6: Pulling from library/centos
fb9cc58bde0c: Pull complete 
a005304e4e74: Pull complete 
f1b10cd84249: Already exists 
Digest: sha256:2d1f734eeef577092fd5d9670bc4e4e6291cbbe2a5b894fcc094f6a95623ba9f
Status: Downloaded newer image for centos:centos6
~~~

### コンテナにApacheを設定

~~~
# yum update
# yum install httpd
# chkconfig httpd on
# service httpd start
# /etc/init.d/httpd start
Starting httpd: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.8 for ServerName
                                                           [  OK  ]
~~~

### Rubyのインストール

~~~
# yum install -y git tar gcc-c++ openssl-devel readline-devel zlib-devel 

/// install ruby-build
# git clone https://github.com/sstephenson/ruby-build.git
# ruby-build/install.sh
# rm -fr ruby-build

/// install ruby
# ruby-build 2.2.3 /usr/local/
# ruby -v
ruby 2.2.3p173 (2015-08-18 revision 51636) [x86_64-linux]

/// gem
# gem update --system
# gem -v
2.4.8

/// Bundler
# gem install bundler --no-rdoc --no-ri
# bundle -v
Bundler version 1.10.6
~~~

Sinatraをインストールして起動するまで試そうと思ったがとりあえずここまで

進展があったら追記する