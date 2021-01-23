[トップに戻る](../index.md)

# Raspberry Pi における Python
- [こちら参照](https://github.com/draemonash2/wiki/blob/master/lng_python/python_raspberrypi.md) 参照

# ToDo
- 無線LAN がつながらない
- 遠隔からクーラーをOn/Off
	- http://kaiware007.hatenablog.jp/entry/2015/08/28/020356
- リモコンで照明を On/Off
- 人感照明
- トイレのジュークボックス＋人感センサ
- サーバー構築
- [デジタルＩＣ](http://part.freelab.jp/p_iclogic.html)

# Tips
- RaspberryPiログイン方法
	- ★
- Raspberry Pi ⇔ Windows ファイル共有方法
	- ①Raspberry Pi を起動。
	- ②SFTP Net Drive Free を起動し、Connect。
	- ③指定したドライブとしてアクセスできるようになる。
	- SFTP Net Drive Free の設定方法は[こちら](http://vogel.at.webry.info/201312/article_8.html)
- リモートデスクトップでアクセスしたときに、意図したキーが打てない
	- 例）( ⇒ '
	- [手順はこちら](http://www.eonet.ne.jp/~smallbear/X/xrdp-jpkeymap.html)

# コマンド
## Linux 共通コマンド

- [Linuxの基本コマンドはこちら](https://github.com/draemonash2/wiki/blob/master/sft_linux/linux.md)

## Raspberry Pi 関連コマンド

- 【rapsbian 再起動】sudo reboot
- 【rapsbian シャットダウン】sudo shutdown -h now

- 【samba サーバ設定ファイル】/etc/samba/smb.conf
- 【samba 再起動】sudo service smbd restart

# 設定事項

- /etc/network/interfaces

```:/etc/network/interfaces
# Please note that this file is written to be used with dhcpcd.
# For static IP, consult /etc/dhcpcd.conf and 'man dhcpcd.conf'.

auto lo
iface lo inet loopback

auto wlan0
allow-hotplug wlan0
# iface wlan0 inet manual
iface wlan0 inet static
address 192.168.100.52
netmask 255.255.255.0
gateway 192.168.100.1
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

auto eth0
allow-hotplug eth0
iface eth0 inet static
address 192.168.100.52
netmask 255.255.255.0
gateway 192.168.100.1
```

- /etc/wpa\_supplicant/wpa\_supplicant.conf

``` :/etc/wpa_supplicant/wpa_supplicant.conf
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
        # ssid="MyPerfectWimax2Terminal"
        ssid="MyPerfectAirStation"
        # psk="Endo4353"
        psk=b4771d9facdaea4848b6d9502a09d8fef412e174b3680dd24df0b60e4e6c386f
        # proto=RSN
        # pairwise=CCMP
        # key_mgmt=WPA-PSK
        # auth_alg=OPEN
```

- /etc/dhcpcd.conf

``` :/etc/dhcpcd.conf
・
・
・
（省略）
・
・
・

# iface wlan0 inet dhcp
# iface wlan0 inet dhcp
# iface wlan0 inet dhcp
interface wlan0
static ip\_address=192.168.100.52/24
static routers=192.168.100.1
static domain\_name\_servers=192.168.100.1

interface wlan0
static ip\_address=192.168.100.52/24
static routers=192.168.100.1
static domain\_name\_servers=192.168.100.1
```

# 参考 URL

- 【ネットワーク設定】
	- [Raspbian 8.0 (jessie)で無線LANを使う](http://qiita.com/yosi-q/items/c677e4650b22ffffa806)
	- [Raspberry Pi 3 (Raspbian Jessie)の無線LANに固定IPアドレスを設定する](http://qiita.com/momotaro98/items/fa94c0ed6e9e727fe15e)
	- [Raspberry Pi 2 Raspbian Jessie をWi-Fi接続、IP固定にしてhost名でssh接続可能にする](http://qiita.com/laynts/items/b2d7089aaa5ed24dd1bb)
- 【ファイルサーバ化】
	- [第14回 Raspberry Piのファイルサーバ設定をする](https://tool-lab.com/make/raspberrypi-startup-14/)
	- [Raspberry Pi 2 Model Bでファイルサーバを構築してみた](http://俺の技術メモ.net/raspberry-pi-samba/)
	- [Raspberry Pi Model B+のUSBポートに1.2Aの電力を供給する](http://akkiesoft.hatenablog.jp/entry/20140727/1406443999)
	- [Raspberry Piでファイルサーバ、Part2 外付けハードディスクの導入編](http://denshikousaku.net/raspberry-pi-part2-external-hdd)
	- [RaspberryPiのファイルサーバ(Samba)をSMB2対応で高速化](http://blog.bnikka.com/raspberrypi/raspberrypi-samba.html)
- [OS インストール方法](http://techblog.clara.jp/2015/02/raspberry-pi-2-model-b_install_and_ssh_connect/)
	- [⇒ここに Raspbian インストール時の設定も記載。](http://usicolog.nomaki.jp/engineering/raspberryPi/raspberryPi2.html#setupOS)
- SSH 接続
	- [参考１](http://independence-sys.net/main/?p=975o)
		- ⇒これで「IP 固定化」「OS設定」「リモートデスクトップ接続」までは大体いけるはず…
	- [こちら](http://tomoyukim.hatenablog.com/entry/2015/05/23/150612)
	- 上記 URL で出来なかったら以下。
		- [IP 固定（ラズパイ）](http://www.hiramine.com/physicalcomputing/raspberrypi/setup_staticip.html)
		- [IP 固定（Windows）](http://pc-karuma.net/windows8-ip-address-static-setup/)
		- [OSの環境設定](http://usicolog.nomaki.jp/engineering/raspberryPi/raspberryPi2.html)
			- ⇒ ターミナルからの「sudo raspi-config」でいけそう？
			- ⇒ Keyboard Layout はキーボード接続しないと、設定できない。
		- [SSH リモート接続（コンソール＋GUI）](http://techblog.clara.jp/2015/02/raspberry-pi-2-model-b_install_and_ssh_connect/)
			- ⇒おすすめ
		- [他](http://usicolog.nomaki.jp/engineering/raspberryPi/raspberryPi_SSH.html)
		- [他](http://tomoyukim.hatenablog.com/entry/2015/05/23/150612)
		- [他](http://dangerous-animal141.hatenablog.com/entry/2013/11/04/170708)
- 無線 LAN 接続
	- [参考](http://ryus.co.jp/blog/raspberrypi2-3/)
	- [参考](http://denshikousaku.net/raspberry-pi-wifi-lan-usb)
- [日本語入力](http://www.eonet.ne.jp/~smallbear/X/xrdp-jpkeymap.html)
- [SD パーティション拡張](http://tomoyukim.hatenablog.com/entry/2015/05/27/124504)
- VIM インストール
	- [参考１](http://making.mrlittlebig.com/?p=31)
	- [参考２](http://qiita.com/moriyaman/items/44cda5318ad8b5f7a3ae)
	- [参考３](http://tomohikoseven-andre-tomohikoseven.blogspot.jp/2015/08/vimelixir-2.html)
- [Wifi クレードルについて](http://高速通信.net/router/%E3%82%AF%E3%83%AC%E3%83%BC%E3%83%89%E3%83%AB.html)
- [使い方基礎](http://qiita.com/starswirl_k/items/2c4df3c5ef81aec66288)
- [ブラウザで回路設計](https://123d.circuits.io/)
- [フォント変更](http://www.mztn.org/rpi/rpi34.html)
	- sudo apt-get install fonts-vlgothic
- [DNS サーバ設定](http://www.linux-beginner.com/linux_setei2.html)
- CentOS ⇔ Debian 比較
	- [参考１](http://blog.asial.co.jp/819)
	- [参考２](http://www.kotaden.com/index.html)

[トップに戻る](../index.md)
