[トップに戻る](../index.md)

# XCode

## トラブルシューティング

- [「信頼されていないデベロッパ」ダイアログが出た時の対処法](https://qiita.com/nonkapibara/items/d14c796ca69c8a4e58d2)
	- 【解決方法】iPhone上でデベロッパを信頼する
		1. 「設定」-「一般」-「デバイス管理」をタップ
		1. 該当するデバイスを信頼する
- [Developer Mode disabledと表示されて実機ビルドができない](https://qiita.com/tsuzuki817/items/7a631928c03548002fb7)
	- 【解決方法】デベロッパーモードを有効化する
		1. iPhone上で設定アプリを開く
		1. 中間ほどまでスクロールし「プライバシーとセキュリティ」をタップ
		1. さらに最下部までスクロールし、「デベロッパモード」をタップ
		1. デベロッパーモードのトグルスイッチをオン
- [古いXcodeが対応していない新しいバージョンのiOSに対してアプリをRunさせる方法](https://qiita.com/n-funaki/items/213f2e44aad4128a76b7#%E8%BF%BD%E8%A8%98%E3%81%9D%E3%81%97%E3%81%A6%E7%B5%90%E8%AB%9620200702)
	- 【解決方法】対応するiOSのDeviceSupportファイルを格納する
		1. [iPhoneOSDeviceSupportのGitHubリポジトリ](https://github.com/filsv/iPhoneOSDeviceSupport)より該当するiOSバージョンのDeviceSupportファイルを取得する。
		1. DeviceSupportファイルを以下に格納する
			`/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/DeviceSupport/`

[トップに戻る](../index.md)

