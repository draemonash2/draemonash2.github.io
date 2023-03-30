[トップに戻る](../index.md)

# インストール方法

1. Git msysgit をインストール
1. [こちら](http://code.google.coam/p/tortoisegit/wiki/Download)より、Git クライアントのインストールファイルと言語ファイルをダウンロード
1. Git クライアントのインストール
1. 言語ファイルのインストール (各サイトで日本語化方法を紹介しているが、最新版では日本語ファイルをインストールするだけで日本語化が可能)

# Tips

- [Push時、毎回認証画面が表示される対策](https://gist.github.com/stakiran/ab47411c1767e4e26b561925dbc2ddb3)
    1. Tortoise Gitの設定を開く（Git管理対象ファイルを右クリック→Setting）
    1. 「Git」→「全ユーザ共通設定を編集(Y)」を押下
    1. メモ帳にて開かれたgitconfig内の以下項目を変更して保存
        - 変更前：helper = manager
        - 変更後：helper = wincred
    1. 「Git」→「このユーザ共通設定を編集(O)」に対しても、上記と同様の設定を行う

- SSH鍵認証の方法＠Windows
    1. WSL上でSSH鍵認証の設定を行う
        1. [SSH鍵生成＆アップロード](https://www.emb-se.com/?p=496)を行う
            - WSLのホームディレクトリ(`\\wsl$\Ubuntu\home\<UserName>\.ssh`)にid\_rsa.ppkが作られる
    1. Windows上でSSH鍵認証の設定を行う
        1. ホームディレクトリ直下の.sshフォルダ(e.g. C:\Users\<UserName>\.ssh)にid\_rsa.ppkをコピーする
        1. githubのページよりURL取得
            - URL取得時、「SSH」を指定する。
                ![-](githubURL取得.jpg)
        1. gitクローン
            - 作成したid\_rsa.ppkファイルを指定してgitクローンする
                ![-](githubクローン方法.jpg)
- コミットウィンドウ表示
    - `start TortoiseGitProc /command:commit /path:"C:\codes" /logmsg:"mod"`
- [コミットメッセージ変更方法](https://kuttsun.blogspot.com/2017/10/tortoisegit.html)
    - 直前コミットの場合
        - コミットの画面で「最後のコミットをやり直す」にチェックを入れる。
    - ２つ以上前のコミットのメッセージを編集
        - 省略。タイトルのリンク先参照。
- TortoiseGitでコミットしようとすると、エラー `repository path 'xxx' is not owned by current user` が発生する。
    - 事象

        ```shell
        Could not get HEAD hash.
        libgit2 returned: repository path 'C:/programs/' is not owned by current user.
        
        To add an exception for this directory, call:
        git config --global --add safe.directory 'C:/programs/'
        ```

    - 対処方法
        - .gitconfig に safe directory 設定を追加する。
            - 対象： `C:\Users\<UserName>\.gitconfig`
            - 追加内容：

                ```
                [safe]
                    directory = *
                ```

[トップに戻る](../index.md)
