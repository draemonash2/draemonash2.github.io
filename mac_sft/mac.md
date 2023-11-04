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
- [リモートデスクトップ接続（Windows→Mac）＠UltraVNC](https://mebee.info/2019/11/20/post-3187/)
    1. Mac側設定
        1. Apple メニュー -> システム環境設定 をクリックする
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
- 外出先からリモートデスクトップ接続（Windows→Mac）＠RealVNC
    1. Mac側設定
        1. [RealVNC Serverインストール＆設定](https://yama-mac.com/recommend_realvnc_mac/)
        1. VNCAGENT許可
            1. Apple メニュー -> システム環境設定 をクリックする
            1. セキュリティとプライバシー をクリックする
            1. 「画面収録」の `vncagent` にチェックを入れる(※1)
            1. 「アクセシビリティ」の `vncagent` にチェックを入れる(※1)
                - (※1) `vncagent` が表示されない場合は、macを再起動してみる
    1. Windows側設定
        1. [RealVNC Viewerインストール＆接続](https://yama-windows10.com/recommend_realvnc/#toc8)
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

- [日本語入力キー入れ替え](https://bl6.jp/dev/computer/os-x-el-capitan-command-space-from-control-space/)
    - 概要
        - 日本語入力キーである「Ctrl+Space」を「Command+Space」(Spotlight検索)に設定する。  
        (日本語入力キーである「Ctrl+Space」はターミナルのprefixキーと被るため)
    - 手順
        1. Apple メニュー -> システム環境設定 をクリックする
        1. 「キーボード」をクリック
        1. 「ショートカットキー」タブを選択する
        1. 左ペインの「Spotlight」を選択し、右側の「Spotlight 検索を表示」のチェックを外す
        1. 左ペインの「入力ソース」を選択し、右側の「前の入力ソースを選択」のショートカットキーを「Command+Space」に変更する

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
    | IME切替え  | Command + Space (デフォルト：Ctrl + Space) |
    | タブ切替え | Command + Tab   |
    | 行頭移動 | Ctrl + a |
    | 行末移動 | Ctrl + e |
    | 文字削除(カーソル～行末) | Ctrl + k |
    | スクショ | Command + Shift + 3 |
    | スクショ（矩形選択） | Command + Shift + 4 |

- Finder

    | 操作       | キー(Mac)       |
    | :---       | :---            |
    | Finderを起動する | Option + Command + Space |
    | Finderを閉じる | Command + w |
    | ファイル移動 | Command + c → Command + Option + v |
    | 新しいウィンドウを開く | Command + n |
    | 新しいタブを開く | Command + t |
    | ファイル削除 | Command + Delete |

- Safari

    | 操作       | キー(Mac)       |
    | :---       | :---            |
    | 検索バーにフォーカス | Command + l |
    | 次のタブ | Ctrl + Tab |
    | 前のタブ | Ctrl + Shift + Tab |
    | タブを閉じる | Command + w |
    | 最後に閉じたタブを開く | Command + Shift + t |
    | 進む | Command + ] |
    | 戻る | Command + [ |

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

## バージョン一覧

iOS 17上でiPhoneアプリをデバッグするために、mac/macOS/Xcodeのバージョンを以下にまとめる。

- [Mac Mini](https://yama-mac.com/macos_correspondence_table/)

    | モデル名 | 対応macOS | 発売年 |
    | :--- | :--- | :--- |
    | Mac mini (2018) | 10.14 ～ 14.1 | 2018 |
    | **Mac mini (Late 2014)** | 10.1 ～ 12.7.1 | 2014 |
    | … | … | … |

- [macOS（Intel）](https://yama-mac.com/macos_correspondence_table/)

    | macOS 名称 | macOS バージョン | リリース年 |
    | :--- | :--- | :--- |
    | macOS 14 Sonoma | 14.0 ～ 14.1 | 2023 |
    | macOS 13 Ventura | 13.0 ～ 13.6.1 | 2022 |
    | **macOS 12 Monterey** | 12.0 ～ 12.7.1 | 2021 |
    | macOS 11 Big Sur | 11.0 ～ 11.7.10 | 2020 |
    | macOS 10.15 Catalina | 10.15 ～ 10.15.7 | 2019 |
    | macOS 10.14 Mojave | 10.14 ～ 10.14.6 | 2018 |
    | macOS 10.13 High Sierra | 10.13 ～ 10.13.6 | 2017 |
    | macOS 10.12 Sierra | 10.12 ～ 10.12.6 | 2016 |
    | OS X 10.11 El capitan | 10.11 ～ 10.11.6 | 2015 |
    | OS X 10.10 Yosemite | 10.10 ～ 10.10.5 | 2014 |
    | OS X 10.9 Mavericks | 10.9 ～ 10.9.5 | 2013 |
    | … | … | … |

- [Xcode](https://developer.apple.com/jp/support/xcode/)

    | バージョン | 最小macOS | SDK | アーキテクチャ | Deployment Target | シミュレータ | Swift | 備考 |
    | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
    | 15.1 beta | macOS Ventura 13.5 | iOS 17<br>macOS 14<br>tvOS 17<br>watchOS 10<br>DriverKit 23<br>visionOS 1 | i386<br>x86_64<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 12-17.0.1<br>iPadOS 13-17.0.1<br>macOS 10.13-14<br>tvOS 12-17<br>watchOS 4-10<br>DriverKit 19-23<br>visionOS 1 | iOS 14.0.1-17.0.1<br>tvOS 15-17<br>watchOS 7-10<br>visionOS 1 | Swift 4<br>Swift 4.2<br>Swift 5.9 |
    | 15 beta 8 | macOS Ventura 13.4 | iOS 17<br>macOS 14<br>tvOS 17<br>watchOS 10<br>DriverKit 23<br>visionOS 1 | i386<br>x86_64<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 12-17<br>iPadOS 13-17<br>macOS 10.13-14<br>tvOS 12-17<br>watchOS 4-10<br>DriverKit 19-23<br>visionOS 1 | iOS 14.0.1-17<br>tvOS 14-17<br>watchOS 7-10<br>visionOS 1 | Swift 4<br>Swift 4.2<br>Swift 5.9 |
    | 15.0.x | macOS Ventura 13.5 | iOS 17<br>macOS 14<br>tvOS 17<br>watchOS 10<br>DriverKit 23 | i386<br>x86_64<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 12-17<br>iPadOS 13-17<br>macOS 10.13-14<br>tvOS 12-17<br>watchOS 4-10<br>DriverKit 19-23 | iOS 14.0.1-17<br>tvOS 14-17<br>watchOS 7-10 | Swift 4<br>Swift 4.2<br>Swift 5.9 |
    | 14.3.1 | macOS Ventura 13 | iOS 16.4<br>macOS 13.3<br>tvOS 16.4<br>watchOS 9.4<br>DriverKit 22.4 | i386<br>x86_64<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 11-16.4<br>iPadOS 13-16.4<br>macOS 10.13-13.3<br>tvOS 11-16.4<br>watchOS 4-9.4<br>DriverKit 19-22.4 | iOS 13.7-16.4<br>tvOS 13.4-16.4<br>watchOS 7-9.4 | Swift 4<br>Swift 4.2<br>Swift 5.8.1 |
    | 14.3 | macOS Ventura 13 | iOS 16.4<br>macOS 13.3<br>tvOS 16.4<br>watchOS 9.4<br>DriverKit 22.4 | i386<br>x86_64<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 11-16.4<br>iPadOS 13-16.4<br>macOS 10.13-13.3<br>tvOS 11-16.4<br>watchOS 4-9.4<br>DriverKit 19-22.4 | iOS 13.7-16.4<br>tvOS 13.4-16.4<br>watchOS 7-9.4 | Swift 4<br>Swift 4.2<br>Swift 5.8 | [本バージョン以上であれば、iOS17上でデバッグが可能](https://alpha2048.hatenablog.com/entry/2023/10/29/154229) |
    | **14.2** | macOS Monterey 12.5 | iOS 16.2<br>macOS 13.1<br>tvOS 16.1<br>watchOS 9.1<br>DriverKit 22.2 | i386<br>x86_64<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 11-16.2<br>iPadOS 13-16.2<br>macOS 10.13-13.1<br>tvOS 11-16.1<br>watchOS 4-9.1<br>DriverKit 19-22.2 | iOS 12.4-16.2<br>tvOS 12.4-16.1<br>watchOS 7-9.1 | Swift 4<br>Swift 4.2<br>Swift 5.7 |
    | 14.1 | macOS Monterey 12.5 | iOS 16.1<br>macOS 13<br>tvOS 16.1<br>watchOS 9.1<br>DriverKit 22.1 | i386<br>x86_64<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 11-16.1<br>iPadOS 13-16.1<br>macOS 10.13-13<br>tvOS 11-16.1<br>watchOS 4-9.1<br>DriverKit 19-22.1 | iOS 12.4-16.1<br>tvOS 12.4-16.1<br>watchOS 7-9.1 | Swift 4<br>Swift 4.2<br>Swift 5.7 |
    | 14.0.x | macOS Monterey 12.5 | iOS 16<br>macOS 12.3<br>tvOS 16<br>watchOS 9<br>DriverKit 22 | i386<br>x86_64<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 11-16<br>iPadOS 13-16<br>macOS 10.13-12.5<br>tvOS 11-16<br>watchOS 4-9<br>DriverKit 19-22 | iOS 12.4-16<br>tvOS 12.4-16<br>watchOS 7-9 | Swift 4<br>Swift 4.2<br>Swift 5.7 |
    | 13.4 | macOS Monterey 12 | iOS 15.5<br>macOS 12.3<br>tvOS 15.4<br>watchOS 8.5<br>DriverKit 21.4 | i386<br>x86_64<br>armv7<br>armv7s<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 9-15.5<br>iPadOS 13-15.5<br>macOS 10.9-12.3<br>tvOS 9-15.4<br>watchOS 2-8.5<br>DriverKit 19-21.4 | iOS 12.4-15.5<br>tvOS 12.4-15.4<br>watchOS 7-8.5 | Swift 4<br>Swift 4.2<br>Swift 5.6 |
    | 13.3 | macOS Monterey 12 | iOS 15.4<br>macOS 12.3<br>tvOS 15.4<br>watchOS 8.5<br>DriverKit 21.4 | i386<br>x86_64<br>armv7<br>armv7s<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 9-15.4<br>iPadOS 13-15.4<br>macOS 10.9-12.3<br>tvOS 9-15.4<br>watchOS 2-8.5<br>DriverKit 19-21.4 | iOS 12.4-15.4<br>tvOS 12.4-15.4<br>watchOS 7-8.5 | Swift 4<br>Swift 4.2<br>Swift 5.6 |
    | 13.2 | macOS Big Sur 11.3 | iOS 15.2<br>macOS 12.1<br>tvOS 15.2<br>watchOS 8.3<br>DriverKit 21.2 | i386<br>x86_64<br>armv7<br>armv7s<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 9-15.2<br>iPadOS 13-15.2<br>macOS 10.9-12.2<br>tvOS 9-15.2<br>watchOS 2-8.3<br>DriverKit 19-21.2 | iOS 10.3.1-15.2<br>tvOS 10.2-15.2<br>watchOS 3.2-8.3 | Swift 4<br>Swift 4.2<br>Swift 5.5 |
    | 13.1 | macOS Big Sur 11.3 | iOS 15<br>macOS 12<br>tvOS 15<br>watchOS 8<br>DriverKit 21.0.1 | i386<br>x86_64<br>armv7<br>armv7s<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 9-15<br>iPadOS 13-15<br>macOS 10.9-12<br>tvOS 9-15<br>watchOS 2-8<br>DriverKit 19-21.0.1 | iOS 10.3.1-15<br>tvOS 10.2-15<br>watchOS 3.2-8 | Swift 4<br>Swift 4.2<br>Swift 5.5 |
    | 13 | macOS Big Sur 11.3 | iOS 15<br>macOS 11.3<br>tvOS 15<br>watchOS 8<br>DriverKit 20.4 | i386<br>x86_64<br>armv7<br>armv7s<br>armv7k<br>arm64<br>arm64e<br>arm64_32 | iOS 9-15<br>iPadOS 13-15<br>macOS 10.9-11.3<br>tvOS 9-15<br>watchOS 2-8<br>DriverKit 19-20.4 | iOS 10.3.1-15<br>tvOS 10.2-15<br>watchOS 3.2-8 | Swift 4<br>Swift 4.2<br>Swift 5.5 |

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
