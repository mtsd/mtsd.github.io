Wireshark


## Wiresharkのインストール

### XQuartzのインストール

[XQuartz](http://xquartz.macosforge.org/landing/)

### Wiresharkのインストール

[Wireshark](https://www.wireshark.org/download.html)

## Remote Virtual Interface(RVI)の作成

* [WiresharkでiPhoneの通信をトレースする](http://wonderpla.net/blog/engineer/Wireshark_iPhone/)

Macに実機を繋いで、RVIを作成する

~~~
$ rvictl -S UDID

Starting device UDID [SUCCEEDED] with interface rvi0

$ ifconfig -l
lo0 gif0 stf0 en0 en1 en2 en3 p2p0 awdl0 bridge0 rvi0
~~~

不要になったらRVIを破棄

~~~
$ rvictl -X UDID

Stopping device UDID [SUCCEEDED]
~~~

## Filter

* urlに特定のパスを含む

~~~
http.request.uri contains "/test"
~~~
