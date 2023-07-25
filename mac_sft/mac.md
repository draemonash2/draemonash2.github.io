# Mac

[トップに戻る](../index.md)

XCodeについては[こちら](../xcode_sft/xcode.md)を参照。

## 設定

macOS Monterey 12.6.7 上での設定手順を以下に示す。

- [起動音無効化](https://support.apple.com/ja-jp/HT211996)
    1. Apple メニュー -> システム環境設定 -> サウンド をクリック
    1. 「サウンドエフェクト」パネルの「起動時にサウンドを再生」を設定する
- [ディスプレイ回転](https://www.eizo.co.jp/support/compati/monitor/rotation/macosx.html)
    1. Apple メニュー -> システム環境設定 -> ディスプレイ をクリック
    1. 「ディスプレイ」タブの「回転」を設定する
- [マウスホイール反転](https://mac-windows-pc.com/scroll-natural)
    1. Apple メニュー -> システム環境設定 -> トラックパッド -> スクロールとズーム をクリック
    1. 「スクロールの方向:ナチュラル」のチェックを外す
- [スリープ抑制](https://itojisan.xyz/settings/32800/)
    1. Apple メニュー -> システム環境設定 -> 省エネルギー をクリック
    1. 左ペインで「電源」を選択
    1. 右ペインの「ディスプレイをオフにする」のスライダーを一番右(「しない」)に移動
- [リモートデスクトップ接続](https://mebee.info/2019/11/20/post-3187/)
    1. Mac側設定
        1. アップルマーク -> システム環境設定 をクリックする
        1. 共有 をクリックする
        1. 左の「画面共有」にチェックを入れる
        1. アクセス許可に「すべてのユーザ」を選択する
        1. 右中央にある「コンピュータ設定」をクリックする
        1. 両方にチェックを入れてパスワードを入力する
    1. Windows側設定
        1. [UltraVNC Viewer](https://forest.watch.impress.co.jp/library/software/ultravnc/)インストール
            - インストールソフトを「Viewer」のみにする
        1. UltraVNC Viewer 起動
            1. Auto Scalingにチェックを入れる
            1. 「options…」をクリックする
            1. 「Scale to window」にチェックを入れ、「ok」をクリックする
            1. 接続先のmacのipアドレスを入力し、「connect」をクリックする
            1. mac側で設定したパスワードを入力して接続する
- [ログインシェル変更bash化](https://www.task-notes.com/entry/20150117/1421482066)
    1. ターミナルを開く
    1. `chsh -s /bin/bash` を実行する
        - 注意：自動的に.bashrcが読み込まれない場合は、以下の内容の.bash_profileを作成する。

            ```shell
            if [ -f ~/.bashrc ] ; then
              . ~/.bashrc
            fi
            ```

- [universal-ctagsインストール](https://formulae.brew.sh/formula/universal-ctags)
    1. ターミナルを開く
    1. 以下のコマンドを実行する

        ```shell
        brew unlink ctags
        brew install universal-ctags
        ```

## キーボード

- [Mac⇔Windows間キー対応表](https://mac-windows-pc.com/mac-windows-keyboard)
    - MacにWindowsキーボードを接続した場合の割り当てキー

        | Windows    | Mac     |
        | :---       | :---    |
        | Win        | command |
        | Alt        | option  |
        | BackSpace  | delete  |
        | バックスラッシュ  | option + ¥  |

- その他キー対応

    | 操作       | キー(Mac)       |
    | :---       | :---            |
    | IME切替え  | Command + Space |
    | タブ切替え | Command + Tab   |
    | 行頭移動 | Ctrl + a |
    | 行末移動 | Ctrl + e |
    | 文字削除(カーソル～行末) | Ctrl + k |
    | スクショ | Command + Shift + 3 |
    | スクショ（矩形選択） | Command + Shift + 4 |

- Finder 関連

    | 操作       | キー(Mac)       |
    | :---       | :---            |
    | Finderを起動する | Option + Command + Space |
    | Finderを閉じる | Command + w |
    | ファイル移動 | Command + c → Command + Option + v |
    | 新しいウィンドウを開く | Command + n |
    | 新しいタブを開く | Command + t |
    | ファイル削除 | Command + Delete |

## Tips

- SSH接続方法
    - `ssh tatsuyaendo@192.168.0.25`
- Majestouch BlackはMacで使えるか？
    - [使える (iMac用OS8.1以降対応)](https://www.diatec.co.jp/support/s-mac.php)
- MX Master3sはMacで使えるか？
    - [使える（macOS 10.15 以降）](https://www.logicool.co.jp/ja-jp/products/mice/mx-master-3s.910-006567.html)
- Mac上でLinuxを動かせるか？
    - 動かせる。そもそもMacはLinux(UNIX？)で作られているため、何もしなくても動く。
- [macOSのバージョン一覧](https://pc-karuma.net/mac-os-x-version/)

## トラブルシューティング

### ターミナル

- ログインシェルをbashに変更したい
    - `chsh -s /bin/bash` を実行する
- 自動的に `.bashrc` が読み込まれない
    - 以下の内容の `.bash_profile` を作成する。

        ```shell
        if [ -f ~/.bashrc ] ; then
          . ~/.bashrc
        fi
        ```

- ctagsで/usr/bin/local/ctagsを実行できるようにしたい
    - `PATH=${PATH}:/usr/local/bin`を実行する
- tmux×vimでハイライトされない
    - `~/.tmux.conf` に以下を設定する `set -g default-terminal "screen-256color"`
- vimで:Gpが効かない
    - `.vimrc` の `g:sGrepFileExt` に `*.swift` を追加する
- tmuxでログインするとbashに切り替えられない
    - ログインシェル変更＋ `.bash_profile` 作成により解決
- .bashrcが読み込まれない
    - ログインシェル変更＋ `.bash_profile` 作成により解決
- .bashrcで設定したプロンプトにならない
    - [~/.tmux.confに以下を設定する](https://gist.github.com/bbqtd/a4ac060d6f6b9ea6fe3aabe735aa9d95#the-fast-blazing-solution)
        - `set -g default-terminal "screen-256color"`

[トップに戻る](../index.md)
