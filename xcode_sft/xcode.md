# XCode

[トップに戻る](../index.md)

## ショートカットキー

| 操作       | キー(Mac)       |
| :---       | :---            |
| 置換(ファイル内すべて) | Option + Command + f → 置換文字列を設定 → 「All」をクリック |
| 置換(選択範囲内) | Option + Command + f → 置換文字列を設定 → Optionキーを押しながら「All in Selection」をクリック |
| 矩形選択＠マウス | Option + マウスドラッグ |
| 矩形選択＠キーボード | Shift + Ctrl + マウスドラッグ |

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
- エラー `ld: framework not found Alamofire` が発生する
	- 解決方法：「Project -> Build Settings -> Other Linker Flags」から `-framework "Alamofire"` を全て削除する。[[1]](https://zenn.dev/luigi_06/articles/b40c1088d7b759)

## バージョン一覧

[Mac](../mac_sft/mac.md)のWikiページ参照。

## Tips

- アプリを作るだけなら無料か？
    - 無料。アプリを公開するのは有料。
- [iPhoneアプリ開発 最小要件](https://coolio.co.jp/column/20230317-1790/)
    - プロセッサー：Intel Core i5以上
    - メモリ：8GB以上
    - ストレージ：256GB以上のSSD
    - ディスプレイ：解像度1920×1080以上
    - グラフィックス：Intel HD Graphics 6000以上
    - OS：macOS X以上
- iPhoneアプリ開発 動作確認バージョン
    - [macOS](https://pc-karuma.net/mac-os-x-version/)：macOS Monterey 12.6.7
    - [XCode](https://www.techgaku.com/system-requirements-of-xcode)：13.4.1
    - iOS：iOS 16.5.1
    - 機種：iPhone 12 Pro Max
- [iPhone アプリ開発集中講座](https://www.amazon.co.jp/SwiftUI-%E6%97%A5%E3%81%A7%E3%83%9E%E3%82%B9%E3%82%BF%E3%83%BC%E3%81%A7%E3%81%8D%E3%82%8B-iPhone-%E3%82%A2%E3%83%97%E3%83%AA%E9%96%8B%E7%99%BA%E9%9B%86%E4%B8%AD%E8%AC%9B%E5%BA%A7-Xcode-ebook/dp/B09JSKHB8L/ref=tmm_kin_swatch_0?_encoding=UTF8&qid=&sr=) 対応スペック
    - mac OS Big Sur 11.3以降
    - XCode 13.0以上
    - iOS 15.0以上

[トップに戻る](../index.md)
