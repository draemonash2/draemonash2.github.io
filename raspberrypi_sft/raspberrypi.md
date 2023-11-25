[トップに戻る](../index.md)

# 関連リンク

- [Linux](../linux_os/linux.md)
- [WSL2](../wsl2_sft/wsl2.md)

# Python＠Raspberry Pi
- [こちら参照](../python_lng/python_raspberrypi.md) 参照

# Tips
- [OSインストール方法](https://www.indoorcorgielec.com/resources/raspberry-pi/raspberry-pi-os%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB/)
- [リモートアクセス＠SSHパスワード方式](https://bright-east-blog.com/skill-up/raspberrypi-ssh-login-setting#toc3)
	1. Raspberry Pi側のSSH有効化する。
	1. Windows を Raspberry Pi と同じネットワークに接続する。
	1. Windows から ping で Raspberry Pi を探す。(応答がなかったら接続できていない）
		- `ping raspberrypi.local`
	1. TeraTerm を起動してSSH接続する。
		1. 「raspberrypi.local」にアクセスする。
		1. ユーザ名、パスワードを入力してアクセス。
			- ユーザ名：pi
			- パスワード(初期)：raspberry
- リモートアクセス＠SSH公開鍵認証方式
	1. 「リモートアクセス＠SSHパスワード方式」でログインできるようにしておく
	1. [こちらのリンク](https://webkaru.net/linux/tera-term-ssh-login-public-key/)の手順で設定する
- [TeraTermから自動でログイン](https://teraterm.jp/?p=37)
	1. 以下のコマンドを書いた「.ttl」ファイルを作成する。
		`connect 'raspberrypi.local /ssh /auth=password /user=pi /passwd=********'`
	1. 上記「.ttl」ファイルを「TeraTerm\ttpmacro.exe」にて実行する。
- [ディスプレイを回転させる](https://lunaticsol.wordpress.com/2018/01/24/%E3%83%A9%E3%82%BA%E3%83%91%E3%82%A4%E3%81%AE%E7%94%BB%E9%9D%A2%E3%82%92%E5%9B%9E%E8%BB%A2%E3%81%95%E3%81%9B%E3%82%8B/)
	1. /boot/config.txt を編集
		- `sudo nano /boot/config.txt`
	1. 末尾に以下の設定を追加
		- `display_rotate=1`
			- 0 = 0°、1=90°、2=180°、3=270°
	1. ラズパイを再起動
- [Windows 上で Raspberry Pi ⇔ Windows 間のファイルを共有する](https://denor.jp/windows%E3%81%A8raspberry-pi%E3%81%AE%E9%96%93%E3%81%A7%E7%B0%A1%E5%8D%98%E3%81%AB%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E8%BB%A2%E9%80%81%E3%83%BB%E3%83%95%E3%82%A9%E3%83%AB%E3%83%80%E5%90%8C%E6%9C%9F)
	1. Raspberry Pi を起動。
	1. 「WinSCP」を起動し、接続。
		- 転送プロトコル：SFTP
		- ホスト名：raspberrypi.local
		- ポート番号:22
		- ユーザ名：pi
		- パスワード：必要に応じて入力
	1. 指定したドライブとしてアクセスできるようになる。
- [リモートデスクトップでアクセスしたときに、意図したキーが打てない](http://www.eonet.ne.jp/~smallbear/X/xrdp-jpkeymap.html)
	- 例）( ⇒ '
- [Raspberry Piにホスト名でアクセスできない時](https://tech-note-meeting.com/2020/08/14/post-316/)

# Linux 共通コマンド

- [Linuxの基本コマンドはこちら](../linux_os/linux.md)

# Raspberry Pi 関連コマンド

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

- [使い方基礎](http://qiita.com/starswirl_k/items/2c4df3c5ef81aec66288)
- 【ネットワーク設定】
	- [Raspberry Pi 3 (Raspbian Jessie)の無線LANに固定IPアドレスを設定する](http://qiita.com/momotaro98/items/fa94c0ed6e9e727fe15e)
	- [Raspberry Pi 2 Raspbian Jessie をWi-Fi接続、IP固定にしてhost名でssh接続可能にする](http://qiita.com/laynts/items/b2d7089aaa5ed24dd1bb)
- 【ファイルサーバ化】
	- [第14回 Raspberry Piのファイルサーバ設定をする](https://tool-lab.com/make/raspberrypi-startup-14/)
	- [Raspberry Pi 2 Model Bでファイルサーバを構築してみた](http://俺の技術メモ.net/raspberry-pi-samba/)
	- [Raspberry Pi Model B+のUSBポートに1.2Aの電力を供給する](http://akkiesoft.hatenablog.jp/entry/20140727/1406443999)
	- [Raspberry Piでファイルサーバ、Part2 外付けハードディスクの導入編](http://denshikousaku.net/raspberry-pi-part2-external-hdd)
	- [RaspberryPiのファイルサーバ(Samba)をSMB2対応で高速化](http://blog.bnikka.com/raspberrypi/raspberrypi-samba.html)
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
- [日本語入力](http://www.eonet.ne.jp/~smallbear/X/xrdp-jpkeymap.html)
- [SD パーティション拡張](http://tomoyukim.hatenablog.com/entry/2015/05/27/124504)
- VIM インストール
	- [参考１](http://making.mrlittlebig.com/?p=31)
	- [参考２](http://qiita.com/moriyaman/items/44cda5318ad8b5f7a3ae)
	- [参考３](http://tomohikoseven-andre-tomohikoseven.blogspot.jp/2015/08/vimelixir-2.html)
- [ブラウザで回路設計](https://123d.circuits.io/)
- [フォント変更](http://www.mztn.org/rpi/rpi34.html)
	- sudo apt-get install fonts-vlgothic
- [DNS サーバ設定](http://www.linux-beginner.com/linux_setei2.html)
- CentOS ⇔ Debian 比較
	- [参考１](http://blog.asial.co.jp/819)
	- [参考２](http://www.kotaden.com/index.html)

# ToDo
- 遠隔からクーラーをOn/Off
	- http://kaiware007.hatenablog.jp/entry/2015/08/28/020356
- リモコンで照明を On/Off
- 人感照明
- トイレのジュークボックス＋人感センサ
- サーバー構築
- [デジタルＩＣ](http://part.freelab.jp/p_iclogic.html)

[トップに戻る](../index.md)
