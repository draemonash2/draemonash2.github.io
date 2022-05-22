[トップに戻る](../index.md)

# コマンド

- 【セッション起動】 `tmux`
- 【セッション起動(セッション名指定)】 `tmux new -s <session_name>`
- 【セッション中断】 `Ctrl-b d` # Detach
- 【セッション復帰】 `tmux a`  # Attach
- 【セッション復帰(セッション名指定)】 `tmux a -t <session_name>`
- 【セッション一覧表示】 `tmux list-sessions`
- 【セッション一覧表示】 `Ctrl-b s`
- 【セッション削除(単一)】 `tmux kill-session`
- 【セッション削除(全て)】 `tmux kill-server`
- 【セッション削除(セッション名)】 `tmux kill-session -t <session_name>`
- 【セッション削除】 `exit`
- 【セッション削除】 `Ctrl-d`

- 【接続クライアント確認】 `tmux list-client`

- 【ウィンドウ作成】 `Ctrl-b c` # Create
- 【ウィンドウ移動(次)】 `Ctrl-b n` # Next
- 【ウィンドウ移動(前)】 `Ctrl-b p` # Prev
- 【ウィンドウ移動(前回)】 `Ctrl-b l` # Last
- 【ウィンドウ移動(ウィンドウ番号指定)】 `Ctrl-b 数字`
- 【ウィンドウ移動(ウィンドウ番号指定)】 `Ctrl-b '`
- 【ウィンドウ一覧表示】 `Ctrl-b w` # Window
- 【ウィンドウ名変更】 `Ctrl-b ,`
- 【ウィンドウ番号変更】 `Ctrl-b .`
- 【ウィンドウ削除】 `exit`
- 【ウィンドウ削除】 `Ctrl-d`
- 【ウィンドウ削除 (確認付き)】 `Ctrl-b &`

- 【ペイン分割(水平)】 `Ctrl-b "`
- 【ペイン分割(垂直)】 `Ctrl-b %`
- 【ペインリサイズ】 `Ctrl-b 矢印`
- 【ペイン移動(次)】 `Ctrl-b o`
- 【ペイン移動(前回)】 `Ctrl-b ;`
- 【ペイン番号表示】 `Ctrl-b q`
- 【ペイン順序入替 前/後】 `Ctrl-b {` / `Ctrl-b }`
- 【ペイン最大化・復帰】 `Ctrl-b z`
- 【ペインレイアウト変更】 `Ctrl-b SPACE`
- 【ペイン時計表示 (q で終了)】 `Ctrl-b t`
- 【ペインウィンドウ化】 `Ctrl-b !`
- 【ペイン削除】 `exit`
- 【ペイン削除】 `Ctrl-d`
- 【ペイン削除(確認付き)】 `Ctrl-b x`

- 【コピーモード 開始】 `Ctrl-b [`
- 【コピーモード 終了】 `q`
- 【コピーモード ペースト】 `Ctrl-b ]`
- 【コピーモード カーソル移動 (左/下/上/右)】 `h`/`j`/`k`/`l`
- 【コピーモード スクロールアップ/ダウン】 `Ctrl-u` / `Ctrl-d`
- 【コピーモード ページアップ/ダウン】 `Ctrl-b` / `Ctrl-f`
- 【コピーモード コピー選択開始】 `SPACE`
- 【コピーモード コピー実行】 `ENTER`
- 【コピーモード 矩形モード切替え】 `v`

- 【キーバインド一覧表示】 `Ctrl-b ?`
- 【コマンド入力モード】 `Ctrl-b :`

- 【オプション表示(サーバー)】 `tmux show-options -s`
- 【オプション表示(セッショングローバル)】 `tmux show-options -g`
- 【オプション表示(現在セッション)】 `tmux show-options
- 【オプション表示(ウィンドウグローバルオプション)】 `tmux show-options -wg
- 【オプション表示(ウィンドウグローバルオプション)】 `tmux show-window-options -g
- 【オプション表示(現在ウィンドウ)】 `tmux show-window-options

- 【ペイン間グローバルキー送信 有効】 `tmux set-window-option synchronize-panes on`
- 【ペイン間グローバルキー送信 無効】 `tmux set-window-option synchronize-panes off`

# Tips

- ターミナル,セッション,ウィンドウ,ペイン
	- ターミナル
		- 複数のセッションを持つことができる
	- セッション
		- ひとつのターミナルから複数のセッションを作成することができる。
		- ターミナルを閉じてもセッションは維持される。
		- セッション実行中は画面の下部に緑のステータスバーが表示される。
	- ウィンドウ
		- ひとつのセッションの中で複数のウィンドウを作成し、切り替えながら作業することができる。
		- ウィンドウの一覧は画面下部のステータスバーに 「数字:ウィンドウ名」で表示される。
	- ペイン
		- ひとつのウィンドウをさらに上下左右のペインに分割して操作できる。
- 設定用コマンド
	- bind は bind-keysのエイリアス
	- set は set-optionのエイリアス
	- setw は set-window-option のエイリアス
	- set-window-option は set-option -w のエイリアス

[トップに戻る](../index.md)
