
# gemini-cli

[トップに戻る](../index.md)

## 手順

### インストール

Ubuntu22.04に対するインストール方法は以下の通り。 [[1]](https://japan.zdnet.com/article/35235129/) [[2]](https://github.com/nodesource/distributions#installation-instructions)

```shell
curl -fsSL https://deb.nodesource.com/setup_23.x -o nodesource_setup.sh
sudo -E bash nodesource_setup.sh
sudo apt-get install -y nodejs
sudo npm install -g @google/gemini-cli
```

### アップデート

```shell
sudo npm install -g npm@latest
sudo npm update -g @google/gemini-cli
```

### 実行

```shell
cd /path/to/workspace
gemini
```

## Tips

- Dockerコンテナ内でGoogle認証する
    - 背景
        - Gemini CLIはGoogleアカウント認証する場合、gemini起動後の認証時に自動的にブラウザを開いて認証する。  
        Dockerコンテナ（ヘッドレスコンテナ）の場合、ブラウザが開けないため、認証できない。
    - 認証手順 [[3]](https://qiita.com/nouernet/items/f460e727c725290b3db0) [[4]](http://ockeysprogramming.blog42.fc2.com/blog-entry-2495.html)
        1. Dockerコンテナ内で認証用URLをコピーする
            1. Gemimni CLIをデバッグモードで起動する

                ```shell
                gemini --debug
                ```

            1. 表示される認証用URLをコピーする（例: `https://accounts.google.com/o/oauth2/v2/auth?redirect_uri=...`）
        1. ホスト環境にて認証を行う
            1. ホスト環境上でブラウザを起動する
            1. 認証用URLを開き、認証を完了する
                - 認証に成功すると、`gemini`上で`Authenticated via "oauth-personal".`が表示されて利用できるようになる

[トップに戻る](../index.md)
