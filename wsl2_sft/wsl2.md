
# WSL2

[トップに戻る](../index.md)

## 関連リンク

- [Linux](../linux_os/linux.md)
- [Raspberry Pi](../raspberrypi_sft/raspberrypi.md)
- [Windows Teminal](../winterm_sft/winterm.md)

## インストール方法

1. WSL2インストール
    1. Microsoft Storeより「Windows Subsystem for Linux」をインストールする。
        - 2023/4現在、コンポーネント版とMicrosoft Store版が存在するが、後者に一本化される見込み。[[1]](https://ascii.jp/elem/000/004/120/4120511/)
1. ディストリビューションインストール
    1. Microsoft StoreよりインストールしたいLinuxディストリビューション(例:Ubuntu 22.04 LTS)をインストールする。(※)
        - (※) [Microsoft Store にある「Ubuntu」の違い](https://forest.watch.impress.co.jp/docs/serial/yajiuma/1134055.html)
            - 「Ubuntu」：現行の「Ubuntu LTS」。新しいバージョンがでるたびに更新される。
            - 「Ubuntu XX.XX」：各バージョンのディストリビューション。
1. WSL2インストール事後作業
    1. BIOS上でVirtulization Technologyを有効化する。
        - HPのPCにおける設定方法は以下の通り。
            1. 起動時にF10を連打してBIOS設定を起動する
            2. System Configuuration -> Virtulization Technology を Enable にする
    1. Windowsの機能を有効化する。
        1. スタートメニュー > 「Windowsの機能の有効化」を検索 > 以下を有効化
            - Linux 用 Windows サブシステム
            - 仮想マシンプラットフォーム
        1. OK を押下する
        1. 自動的に再起動

## その他セットアップ手順

- SSH接続
    1. インストール

        ```shell
        sudo apt update
        sudo apt install openssh-server
        sudo systemctl enable ssh
        sudo systemctl start ssh
        ```

    2. [クライアント側(Windows)の設定](https://kaworu.jpn.org/security/ssh%E6%8E%A5%E7%B6%9A%E3%81%8C%E8%87%AA%E5%8B%95%E5%88%87%E6%96%AD%E3%81%95%E3%82%8C%E3%82%8B%E5%A0%B4%E5%90%88%E3%81%AE%E5%9B%9E%E9%81%BF%E6%96%B9%E6%B3%95)を追加する。
        - 追加対象
            - `%USERPROFILE%\.ssh\config`
        - 追加内容

            ```shell
            ServerAliveInterval 300
            ServerAliveCountMax 10
            ```

    3. [サーバー側(Linux)の設定](https://www.xenos.jp/~zen/blog2/index.php/2020/06/14/post-3987/)を追加する。
        - 追加対象
            - `/etc/ssh/sshd_config`
        - 追加内容

            ```shell
            PasswordAuthentication yes
            ClientAliveInterval 300
            ClientAliveCountMax 10
            Port 10022
            ```

    4. sshサービスを再起動する。

        ```shell
        sudo service ssh restart
        ```

    5. WSL2をバックグラウンドで起動するスクリプト `StartupWsl.vbs` をスタートアップに登録する。

        ```vbs
        Set ws = CreateObject("Wscript.Shell")
        ws.run "cmd /c wsl", vbhide
        ```

    6. `StartupWsl.vbs` を実行する。

# Tips

- WSL2 起動方法＠WSL2コンソール
    1. Windows にて「wsl」を検索して起動する
- WSL2 起動方法＠Windows Terminal
    1. Windows Terminal タイトルバーの下矢印をクリック
    1. 起動したいLinuxディストリビューションを選択
- [ディストリビューションのアップデート方法](https://qiita.com/matarillo/items/98d7452967987fe5d633)
- [WSL2コンソールのコピペ方法](https://qiita.com/kenji0x02/items/f77008985818583bf32b)
    - コピー
        - 方法１：テキストを選択してコピー
        - 方法２：テキストを選択してCtrl+Shift+C
            - ただし、設定を有効化する必要あり。
                - 「WSL2コンソールのプロパティ」->「編集」->「編集オプション」->「Ctrl+Shift+C/Vをコピー/貼り付けとして使用する(C)」をチェック
    - ペースト
        - 方法１：右クリック
        - 方法２：Ctrl+Shift+V
- [Linux⇔Windows間のファイルアクセス方法](https://qiita.com/Uchitaso/items/6e0a7859e87bb8bdb527)
    - Windows上でLinuxのファイルにアクセス
        - エクスプローラからアドレス「\\wsl$」にアクセスする
    - Linux上でWindowsのファイルにアクセス
        - 「/mnt/」にアクセスする
- [ワンアクションで WSL2 を管理者権限起動する](https://www.xenos.jp/~zen/blog2/index.php/2020/05/31/post-3944/)
    1. 以下のバッチファイルを作成する。
        - `powershell start-process wt -verb runas`
    1. 上記バッチファイルのショートカットファイルを作成する
    1. 上記ショートカットファイルを管理者権限で実行するように変更する
- OS間のシンボリックリンク挙動
    - linux(wsl2)上でシンボリックリンクを作るとwindows上で使える？
        - 使えない(0kbの不明なファイルが作られる)
    - windows上でシンボリックリンクを作るとlinux(wsl2)上で使える？
        - 問題なく使える
- データ復旧方法
    - 何らかの理由でWSLが起動できなくなり、内部のデータを取り出せなくなった場合のデータ復旧方法は以下の通り。
        - [ext4.vhdxをバックアップ後、WSLを再インストールする](https://loumo.jp/archives/29239)
            1. `ext4.vhdx` を任意の場所にバックアップする。
                - 格納先： `C:\Users\<USER名>\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu_??????\LocalState/ext4.vhdx`
            1. WSL＋インストール済みディストリビューションを再インストールする。
            1. バックアップした `ext4.vhdx` をWSL2にマウントする。
                - `wsl --mount "path\to\ext4.vhdx"  --vhd`
            1. WSL2を起動し、マウントされたディレクトリから、データを取り出す

## トラブルシューティング

- エラー「0x80073cfc」が発生してwslを起動できない

    ```shell
    Installing, this may take a few minutes...
    WslRegisterDistribution failed with error: 0x80073cfc
    Error: 0x80073cfc ??????????????????????????????????????????????????
    
    Press any key to continue...
    ```

    - 対処方法：WSL2を再インストールするしかない。[[2]](https://github.com/microsoft/WSL/issues/10118)  
    データ自体は、上記に記載の「データ復旧方法」にて復旧可能。

## コマンド

- [こちら](../linux_os/linux.md)

## ショートカットキー

- [こちら](../linux_os/linux.md)

[トップに戻る](../index.md)
