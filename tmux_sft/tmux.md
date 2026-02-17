
# TMUX

[トップに戻る](../index.md)

## コマンド＆ショートカットキー（デフォルト）

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

- 【接続クライアント確認】 `tmux list-client` # 接続中のクライアント(=ターミナル)一覧を表示する

- 【ウィンドウ作成】 `Ctrl-b c` # Create
- 【ウィンドウ切替(次)】 `Ctrl-b n` # Next
- 【ウィンドウ切替(前)】 `Ctrl-b p` # Prev
- 【ウィンドウ切替(前回)】 `Ctrl-b l` # Last
- 【ウィンドウ切替(ウィンドウ番号指定)】 `Ctrl-b 数字`
- 【ウィンドウ切替(ウィンドウ番号指定)】 `Ctrl-b '`
- 【ウィンドウ一覧表示】 `Ctrl-b w` # Window
- 【ウィンドウ名変更】 `Ctrl-b ,`
- 【ウィンドウ番号変更】 `Ctrl-b .`
- 【ウィンドウ削除】 `exit`
- 【ウィンドウ削除】 `Ctrl-d`
- 【ウィンドウ削除 (確認付き)】 `Ctrl-b &`

- 【ペイン分割(水平)】 `Ctrl-b "`
- 【ペイン分割(垂直)】 `Ctrl-b %`
- 【ペインリサイズ】 `Ctrl-b 矢印`
- 【ペイン切替(次)】 `Ctrl-b o`
- 【ペイン切替(前回)】 `Ctrl-b ;`
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
- 【オプション表示(現在セッション)】 `tmux show-options`
- 【オプション表示(ウィンドウグローバルオプション)】 `tmux show-options -wg`
- 【オプション表示(ウィンドウグローバルオプション)】 `tmux show-window-options -g`
- 【オプション表示(現在ウィンドウ)】 `tmux show-window-options`

- 【ペイン間グローバルキー送信 有効】 `tmux set-window-option synchronize-panes on`
- 【ペイン間グローバルキー送信 無効】 `tmux set-window-option synchronize-panes off`

## プラグイン

| プラグイン名 | 説明 |
| :--- | :--- |
| `tpm` | プラグイン管理ツール。 |
| `tmux-resurrect` | tmux セッションのレイアウト／実行中コマンド／pane 状態を保存し、後から復元できるようにするプラグイン。 |
| `tmux-continuum` | tmux セッションを"自動で"保存・復元できるようにするプラグイン。<br>tmux-resurrect を前提として動く強化版ユーティリティ。<br>セッションは`~/.local/share/tmux/resurrect`に保存される。 |
| `tmux-sensible` | tmux を「もっと使いやすい初期設定」に変えてくれる、デフォルト改善プラグイン。 |
| `tmux-yank` | tmux でコピーした内容を、システムクリップボードへ 簡単に Yank（コピー） できるようにするプラグイン。 |

## Tips

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
- status line 色設定
    - 参考URL : [tmux の status line の設定方法](https://qiita.com/nojima/items/9bc576c922da3604a72b#attributes-%E3%81%AB%E6%8C%87%E5%AE%9A%E3%81%A7%E3%81%8D%E3%82%8B%E6%96%87%E5%AD%97%E5%88%97)
- [xpanes](https://github.com/greymd/tmux-xpanes)
    - 概要
        - 端末分割＋各々コマンド実行を一回のコマンド入力で行えるようにするソフト
    - インストール方法
        - [こちら](https://github.com/greymd/tmux-xpanes)
    - コマンド例
        - `xpanes -e "top" "vmstat 1" "watch -n 1 free"`
- mac×tmuxでクリップボードコピー＆ペースト
    - 対応しない
        - mac上のターミナルでコピー＆ペーストに対応すると、Teratermからmacへssh接続した場合のコピー＆ペーストに対応できなくなるため
- SSH接続時と標準ターミナル時で設定を分けたい
    - 案１
        - 内容
            - `.tmux.conf`上で、以下のように条件分岐させて同じキーで別の処理を割り当てる

                ```shell
                (uname | grep -q Linux && test "${MYTERM_PRG}" == "TeraTerm"); echo $?
                (uname | grep -q Linux && test "${MYTERM_PRG}" == ""); echo $?
                (uname | grep -q Darwin && test "${MYTERM_PRG}" == "TeraTerm"); echo $?
                (uname | grep -q Darwin && test "${MYTERM_PRG}" == ""); echo $?
                ```

        - 結論
            - 不可能。
        - 理由
            - tmuxは別セッションであっても一つの設定が読み込まれる。  
            例えば、セッションAで設定Aを読み込むとセッションBでも設定Aが読み込まれる。  
            そのため、条件分岐で割り当てたとしても、別セッションに設定が反映されてしまうので、分岐の意味がなくなる。
- tmux-resurrect セッション保存先
    - `./.local/share/tmux/resurrect/last`
- 利用済みディスプレイ番号確認方法
    - 利用済みのディスプレイ番号（他のユーザがディスプレイ番号を利用しているか）を確認する方法は以下の通り。

    ```shell
    $ vncserver -list
    TurboVNC server sessions:
    X DISPLAY #    PROCESS ID
    :1             12345
    :3             23456
    
    $ ps -ef | grep [X]vnc
    endo     1780582 2441732  0 May28 pts/126  00:00:05 /opt/TurboVNC/bin/Xvnc :1 -desktop TurboVNC: robocip-ubuntu:1 (endo) -auth /home/endo/.Xauthority -geometry 1920x1080 -depth 24 -rfbauth /home/endo/.vnc/passwd -x509cert /home/endo/.vnc/x509_cert.pem -x509key /home/endo/.vnc/x509_private.pem -rfbport 5901 -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1 -deferupdate 1 -dridir /usr/lib/x86_64-linux-gnu/dri -registrydir /usr/lib/xorg
    ```

    - ちなみに、何らかの理由でディスプレイ番号が使われている場合、`vncserver`起動時に以下のようなメッセージが表示される

        ```shell
        WARNING: robocip-ubuntu:2 is taken because of /tmp/.X11-unix/X2
        Remove this file if there is no X server robocip-ubuntu:2
        ```

## トラブルシューティング

- キーが効かない
    - f1～f4＠teraterm＋vim
        - 原因
            - `~`が送信されている。F2は`2~`、F3は`3~`。vimの`~`は大文字小文字入れ替え。
        - 対処
            - teraterm のKEYCONFIG.CNFのF1キーをFUNCTION.CNFの設定値に更新する
                - 変更前：XF1=59
                - 変更後：User8=59,0,$1BOP
    - Ctrl + ,＠teraterm＋vim
        - 原因
            - teratermで`ctrl+b`を`ctrl+,`に置き換えているため
        - 処置
            - teraterm キー設定変更
                - [ESC\[nD カーソルを左にn桁移動](https://teraterm.jp/manual/4.68/html/about/ctrlseq.html#CSI)
    - Ctrl + h
        - 原因
            - [c-hをbackspaceとみなすため](https://rcmdnk.com/blog/2015/01/06/computer-tmux/)
        - 処置
            - `BSpace`へ割り当てる
                - 例： `bind Bspace select-pane -L`
    - Ctrl + h＠tmux＋vim
        - 原因
            - [c-hをbackspaceとみなすため](https://rcmdnk.com/blog/2015/01/06/computer-tmux/)
        - 処置
            - `<bs>`へ割り当てる
                - 例： `noremap <bs> 10zh10h`
- tmux上で日本語をコピーすると文字化けする
    - 対処
        - [ターミナルソフトのコピー機能でコピーする](https://teratail.com/questions/320522)
            - teratermの場合、Ctrl+マウス選択
            - terminatorの場合、Shift+マウス選択
- TurboVNC＋Tmuxでテキストコピーできない
    - 原因
        - 環境設定`DISPLAY`の値がずれていることで、正しいXサーバにクリップ操作が届かないため。
    - 対策
        - vncserverをディスプレイ番号が`:1`になるように起動する
    - 備考
        - FIXME: 起動したディスプレイ番号になるよう`DISPLAY`を設定（例: `export DISPLAY=:3`）しても解消しない。

[トップに戻る](../index.md)
