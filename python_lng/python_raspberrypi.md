[トップに戻る](../index.md)

# 基礎
- サンプルプログラム
	``` py 
	import RPi.GPIO as GPIO #①
	GPIO.setmode(GPIO.BCM) #②
	GPIO.setup(4, GPIO.OUT) #③
	GPIO.output(4, GPIO.HIGH) #④
	GPIO.cleanup() #⑤
	```

## サンプルプログラムの処理説明
- ①RPi.GPIOのインポート
- ②ナンバリング設定
	- アクセスするピンの指定方法
		- GPIO.setmode(GPIO.BOARD) # ピン番号（左下から右上までの連番）指定
		- GPIO.setmode(GPIO.BCM) # GPIO番号
- ③GPIOピン方向設定
- ④GPIOピン操作
- ⑤終了処理
	- チャンネル個別の指定も可
		- 例）GPIO.cleanup(1)

# 参考
- GPIO 基礎
	- http://mamerium.com/raspberry-pi-rpi-gpio-basic/
- ラズパイでセンサーのデータを継続的に記録する（ソフトウェア編）
	- http://windvoice.hatenablog.jp/entry/2015/03/04/165820

# TODO
- 無線LAN がつながらない
- 遠隔からクーラーをOn/Off
	- http://kaiware007.hatenablog.jp/entry/2015/08/28/020356
- リモコンで照明を On/Off
- 人感照明
- トイレのジュークボックス＋人感センサ
- サーバー構築
- デジタルＩＣ
	- http://part.freelab.jp/p\_iclogic.html

# Tips
- Raspberry Pi ⇔ Windows ファイル共有方法
	- ①Raspberry Pi を起動。
	- ②SFTP Net Drive Free を起動し、Connect。
	- ③指定したドライブとしてアクセスできるようになる。
	- SFTP Net Drive Free の設定方法は以下参照
		- http://vogel.at.webry.info/201312/article\_8.html
- リモートデスクトップでアクセスしたときに、意図したキーが打てない
	- 例）( ⇒ '
	- 以下手順参照
		- http://www.eonet.ne.jp/~smallbear/X/xrdp-jpkeymap.html

# 参考 URL
- OS インストール方法
	- http://techblog.clara.jp/2015/02/raspberry-pi-2-model-b\_install\_and\_ssh\_connect/
		- ⇒ここに Raspbian インストール時の設定も記載。
	- http://usicolog.nomaki.jp/engineering/raspberryPi/raspberryPi2.html#setupOS
- SSH 接続
	- http://independence-sys.net/main/?p=975o
		- ⇒これで「IP 固定化」「OS設定」「リモートデスクトップ接続」までは大体いけるはず…
	- http://tomoyukim.hatenablog.com/entry/2015/05/23/150612
	- 上記 URL で出来なかったら以下。
		- IP 固定（ラズパイ）
			- http://www.hiramine.com/physicalcomputing/raspberrypi/setup\_staticip.html
		- IP 固定（Windows）
			- http://pc-karuma.net/windows8-ip-address-static-setup/
		- OSの環境設定
			- http://usicolog.nomaki.jp/engineering/raspberryPi/raspberryPi2.html
				- ⇒ ターミナルからの「sudo raspi-config」でいけそう？
				- ⇒ Keyboard Layout はキーボード接続しないと、設定できない。
		- SSH リモート接続（コンソール＋GUI）
			- http://techblog.clara.jp/2015/02/raspberry-pi-2-model-b\_install\_and\_ssh\_connect/
				- ⇒おすすめ
			- http://usicolog.nomaki.jp/engineering/raspberryPi/raspberryPi\_SSH.html
			- http://tomoyukim.hatenablog.com/entry/2015/05/23/150612
			- http://dangerous-animal141.hatenablog.com/entry/2013/11/04/170708
- 無線 LAN 接続
	- http://ryus.co.jp/blog/raspberrypi2-3/
	- http://denshikousaku.net/raspberry-pi-wifi-lan-usb
- 日本語入力
	- http://www.eonet.ne.jp/~smallbear/X/xrdp-jpkeymap.html
- SD パーティション拡張
	- http://tomoyukim.hatenablog.com/entry/2015/05/27/124504
- VIM インストール
	- http://making.mrlittlebig.com/?p=31
	- http://qiita.com/moriyaman/items/44cda5318ad8b5f7a3ae
	- http://tomohikoseven-andre-tomohikoseven.blogspot.jp/2015/08/vimelixir-2.html
- Wifi クレードルについて
	- http://高速通信.net/router/%E3%82%AF%E3%83%AC%E3%83%BC%E3%83%89%E3%83%AB.html
- 使い方基礎
	- http://qiita.com/starswirl\_k/items/2c4df3c5ef81aec66288

[トップに戻る](../index.md)
