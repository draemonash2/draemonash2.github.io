[トップに戻る](../index.md)

# Tips
- 隠しドライブ設定
	- regedit から HKEY\_CURRENT\_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer（HKEY\_LOCAL\_MACHINE のパターンもある…？）を開く。
	- 「編集(E)」→「新規(N)」→「DWORD値(D)」を選択し，名称を「NoDrives」にする。
	- 隠したいドライブのビットを立てた値を「値のデータ」に設定する。(A,Eドライブを隠したいなら「0x11」を設定する)
	- ドライブにアクセスしたい場合はアドレスバーに記入する。(ex. F:\)
- リモートデスクトップで再全画面化
	- リモートデスクトップを起動後、ウィンドウを小さくすると全画面化ができなくなる。
	- 以下のコマンドで再全画面が可能
		- Ctlr + Alt + Break
- レジストリバックアップ
	- regedit にてバックアップのフォルダで右クリック⇒エクスポート
- フルパスコピー
	- エクスプローラーでファイル選択後、Shift+右クリック⇒パスとしてコピー
- Excel 2003 形式のファイルを右クリックで新規作成できるようにする
	- 「C:\Windows\ShellNew」配下に「excel8.xls」を作成する
	- regedit にて以下のキーを作成する
		- パス：`HKEY_CLASSES_ROOT\.xls\Excel.Sheet.8\ShellNew`
		- 名前：FileName（文字列値）
		- 値のデータ：excel8.xls
	- 再起動
- Windows 8 タッチスクリーン無効
	- デバイスマネージャーを開く
	- ヒューマンインターフェースデバイス
	- HID準拠タッチスクリーンを開いて、「デバイスを無効にする」をクリック
- Windows 8 左端スワイプのチャーム無効＠Vaio
	- 「VAIOの設定」で無効にする
- Windows 10 「システムと圧縮メモリ」を無効にする
	- 「サービス」->「Superfetch」->「サービスの状態」を"停止"に変更
	- 「サービス」->「Superfetch」->「スタートアップの種類」を"手動"に変更
	- ↓参考↓
		- http://komaretel.net/pc/windows10/system-compressram-compression-store/
- Windows 10で起動時のパスワード入力を省略する方法
	- https://121ware.com/qasearch/1007/app/servlet/relatedqa?QID=017735
- VAIO 明るさ自動調整
	- [画面の明るさが自動で変化して見辛い！ 『VAIO Pro 13』の落とし穴を塞げっ！！](http://blogs.yahoo.co.jp/wrp_sony/66813302.html)
- デスクトップアイコン非表示
	- デスクトップ上で右クリック ⇒ 「表示」 ⇒ 「デスクトップアイコンの表示」をクリック
- タスクマネージャーの「スタートアップ」タブのプログラムを削除したい場合。
	- ① 以下フォルダ内にある該当のプログラムショートカットを削除する。
		- C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp
		- %USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
	- ② レジストリエディタにて、以下フォルダ内の該当のキーを削除する。
		- `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\run`
		- `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\run`
- [Windows 10 文字のにじみ解消方法](https://elecot.com/windows10-display-blur)
- [信頼性モニター](https://www.atmarkit.co.jp/ait/spv/1906/06/news014.html)
	- 信頼性モニターでPCの安定性をチェック
		1. ［コントロールパネル］-［セキュリティとメンテナンス］の右ペインにある「メンテナンス」
		1. 「問題の報告」項目にある「信頼性履歴の表示」をクリック
- ショートカットファイルのショートカットキーが効く場所
	- `C:\Users\draem\AppData\Roaming\Microsoft\Windows\Start Menu\Programs`
	- `C:\Users\<User名>\Desktop`
- [キーボード操作が軽快になるよう設定する](https://president.jp/articles/-/28517?page=4)
	1. コントロールセンター -> キーボード
	1. 速度タブ -> 「表示までの待ち時間」を「右端」に移動
- [プリンタがつながらない場合](https://kuritaroh.com/2018/09/01/printerngprint/)
- テンポラリフォルダパス
	- `C:\Users\<ユーザー名>\AppData\Local\Temp`
- Bluetooth テザリング方法＠Windows10
	1. 接続するデバイスと Bluetooth 接続する
	1. Win + R
	1. 「control printers」を実行
	1. テザリング接続するデバイスを選択して右クリック
	1. 「接続方法(C)」→「アクセスポイント(A)」
- 英語ファイルパス メリット
	- 日本語ファイルパスでは動かない環境がある
	- 英語名前付けの練習になる
- 「ファイル名を指定して実行」で管理者権限で起動する方法
	- プログラム名を指定して「Ctrl+Shift+Enter」を押下
- 仮想デスクトップについて
	- デスクトップの移動のアニメーションを抑制したい
		- [こちら](https://jw7.org/2015/11/03/windows10_virtualdesktop_animation_off/)で抑制できる。ただし、最大/最小のアニメーションも抑制されてしまう。
	- 挙動調査
		- 同じプログラムを別のデスクトップに分けられる？
			- 分けられる！ただし、同プロセスで起動しているとみなされる
		- デスクトップ1にてファイルが開いている状態で、デスクトップ2にてファイルを起動したら、もう一つ起動するのか？
			- 起動しない。デスクトップ1に移動してファイルをアクティブにする
	- 別デスクトップへウィンドウを移動する方法
		1. 移動先デスクトップを選択
		1. 移動元デスクトップをマウスポインタで選択
		1. 移動したいウィンドウを右クリック
		1. 「移動先」から移動先デスクトップを選択
- スクリーンショット比較

| キー | 範囲 | 保存先 |
|:---|:---|:---|
| Win + Shift + s（「Snipping Tool」の進化版） | 任意の範囲(矩形選択orディスプレイorウィンドウ)  | クリップボード |
| Win + PrtSc | 全てのディスプレイ | Pictures\スクリーンショット |
| Win + Alt + PrtSc | アクティブウィンドウ | Videos\Captures |
| PrtSc | 全てのディスプレイ | クリップボード |
| Alt + PrtSc | アクティブウィンドウ | クリップボード |
| Ctrl + PrtSc（＠Easy Shot） | アクティブディスプレイ | 任意の場所(クリップボードorデスクトップ) |
| Ctrl + Alt + PrtSc（＠Easy Shot） | アクティブウィンドウ | 任意の場所(クリップボードorデスクトップ) |
| Alt + PrtSc（＠Easy Shot） | 矩形選択範囲 | 任意の場所(クリップボードorデスクトップ) |

- 環境変数の入れ子の振舞い
	- ユーザ環境変数
		- 環境変数「追加」時、即座に展開される
	- システム環境変数
		- 環境変数「参照」時、展開される

# トラブルシューティング
- ファイルの関連付けができない＠windows 7
	- 概要
		- ファイルを開くプログラムの選択にプログラムが表示されない場合の修正方法。
		- 表示されない原因は、ファイルパスを変更した際にレジストリの値が反映していないことが多い。
	- 対処方法
		1. 「スタートメニュー」の「ファイルとプログラムの検索」フォームに「regedit」と入力。
		1. 「regedit.exe」を起動する。
		1. 表示されないプログラムのファイル名を検索する。
		1. レジストリキーの「open」配下にある、ファイルパスの設定値を正しいパスに直す。
- かな入力関連
	- 対処方法
		1. [Caps Lock] キーを押したときに、半角アルファベット入力 [A] する
		1. Microsoft IMEのﾌﾟﾛﾊﾟﾃｨ => オートコレクト タブ => 全角/半角 => 英字⇒常に半角に変換
		1. エディタにて、日本語入力 [あ] 状態で「あ」[Caps Lock] キー「ａ」と入力、変換し半角の「a」で確定します。
- explorerの検索で数字列が引っかからない。(ex. 「20210405」)
	- 原因：不明…
	- 解決策：検索単語に[「~=」を付与](https://did2memo.net/2014/03/07/windows-file-search-unsearchable-number/)する。(ex. 「~=20210405」)
- [Windowsの4Kスケーリング環境を検証する](https://pc.watch.impress.co.jp/docs/column/4kshugyousou/732083.html)

# ショートカットキー

|Ctrl|Shift|Alt|key|機能|
|:---|:---|:---|:---|:---|
|Ctrl|||E|検索バーを開く|
|Ctrl|||F|検索ユーティリティを開始する|
|Ctrl|||H|履歴バーを開く|
|Ctrl|||I|お気に入りバーを開く|
|Ctrl|||L|[ファイルを開く]ダイアログボックスを開く|
|Ctrl|||N|同じWebアドレスで別のブラウザのインスタンスを開く|
|Ctrl|||O|[ファイルを開く]ダイアログボックスを開く。CtrlLキーと同じ|
|Ctrl|||P|[印刷]ダイアログボックスを開く|
|Ctrl|||R|現在のWebページを更新する|
|Ctrl|||W|現在のウィンドウを閉じる|
|Ctrl|||F4キー|複数の文書を同時に開くことができるプログラムで、作業中の文書を閉じる|
|Ctrl|||項目をドラッグする|ファイルをコピーする|
|Ctrl|||Esc|[スタート]メニューを表示する|
|Ctrl|Shift||方向キー|テキストブロックを強調表示する|
|Ctrl|Shift||項目をドラッグする|選択した項目へのショートカットを作成する|
||Shift||Del|選択した項目を、ごみ箱に移動せずに完全に削除する|
||Shift||F10|選択した項目のショートカットメニューを表示する|
||||Enter|選択した項目のプロパティを表示する|
||||Space|作業中のウィンドウのショートカットメニューを開く|
||||Tab|開いている項目を切り替える|
||||Esc|項目を開いた順に切り替える|
||||Space|作業中のウィンドウのシステムメニューを開く|
||||F4|使用中の項目を閉じる、または作業中のプログラムを終了する|
||||メニュー内の下線付きの文字キー|対応するメニューを表示する|
||||F2|選択した項目の名前を変更する|
||||F3|ファイルまたはフォルダを検索する|
||||F4|マイコンピュータまたはエクスプローラでアドレスバーの一覧を表示する|
||||F5|作業中のウィンドウを更新する|
||||F6|ウィンドウ内またはデスクトップ上の画面要素を切り替える|
||||F10|作業中のプログラムのメニューバーをアクティブにする|
||||Left/Right|左/右側のメニューを開く、またはサブメニューを開く|
||||BackSpace|マイコンピュータまたはエクスプローラで1階層上のフォルダを表示する|
|||Win|Pause|システムのプロパティを表示|
|||Win|F|検索ウィンドウを表示|
|Ctrl||Win|D|【仮想デスクトップ】新規デスクトップ作成|
|Ctrl||Win|Left/Right|【仮想デスクトップ】デスクトップに移動 前/次|
|||Win|Tab|【仮想デスクトップ】タスクビュー表示|
|||Win|h|表示 共有チャーム|
|||Win|b|通知領域（タスクトレイ）へフォーカス|
|||Win|t|タスクバー 巡回|
|||Win|x|表示 アドバンスドメニュー(スタートメニューの右クリックメニュー)|
|||Win|z|表示 アプリのコマンドバー|
|||Win|d|表示 デスクトップ|
|||Win|,|表示 デスクトップ(一時的)|
|||Win|PrtSc|スクリーンショット保存 to \\Pictures\\Screenshots|

# 「ファイル名を指定して実行」で開けるフォルダ

[参考URL](https://www.ka-net.org/blog/?p=8432)

| コマンド | フォルダ |
|:---|:---|
| shell:desktop | デスクトップ |
| shell:start menu | スタートメニュー |
| shell:sendto | 送るフォルダ |
| shell:appdata | AppData |
| shell:profile | ユーザー |
| shell:programs | プログラム |
| shell:startup | スタートアップ |
| shell:recyclebinfolder | ごみ箱 |

# ショートカットキー検討

| カテゴリ | 記号 | ショートカットキー（由来） |
|:--|:--:|:---|
| 記号 | ★ | ｓｆ（StarFill）              |
| 記号 | ☆ | ｓｂ（StarBlank）             |
| 記号 | ▲ | ｔｆ（TriangleFill）          |
| 記号 | △ | ｔｂ（TriangleBlank）         |
| 記号 | ▼ | ｖｆ（inVertedtriangleFill）  |
| 記号 | ▽ | ｖｂ（inVertedtriangleBlank） |
| 記号 | ● | ｃｆ（CircleFill）            |
| 記号 | ○ | ｃｂ（CircleBlank）           |
| 記号 | ◎ | ｃｄ（CircleDouble）          |
| 記号 | ■ | ｑｆ（sQuareFill）            |
| 記号 | □ | ｑｂ（sQuareBlank）           |
| 記号 | ◆ | ｒｆ（RhombusFill）           |
| 記号 | ◇ | ｒｂ（RhombusBlank）          |
| ○× | ○ | ｍｒ（MaRu）                  |
| ○× | × | ｂｔ（BaTsu）                 |
| 演算 | × | ｋｒ（KakeRu）                |
| 演算 | ÷ | ｗｒ（WaRu）                  |
| 点   | … | ｔｐ（TreePoint）             |
| 矢印 | ← | ｇｈ                          |
| 矢印 | → | ｇｌ                          |
| 矢印 | ↓ | ｇｊ                          |
| 矢印 | ↑ | ｇｋ                          |
| 矢印 | ⇔ | ｇｈｌ                        |

[トップに戻る](../index.md)