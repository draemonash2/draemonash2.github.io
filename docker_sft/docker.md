
# Docker

[トップに戻る](../index.md)

## インストール手順

[Docker ドキュメント](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository) のインストール手順に従い、docker-ceをインストールする。  
なお、WSL2 へのインストール手順は、ネイティブLinuxへのインストール手順と同じ。

## Docker コマンド

Docker コマンドの一覧は以下の通り。[[1]](https://qiita.com/kattoyoshi/items/c6b731c7eff79becdc61#2-docker-%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E5%85%A8%E4%BD%93%E5%83%8F)

### 全体像

![docker_cmd_overall.jpg](./data/docker_cmd_overall.jpg)

### コマンド一覧

- image の操作
	- 【イメージ確認】 `docker images`
	- 【公開イメージ検索】 `docker search <image>`
	- 【公開イメージ取得】 `docker pull <image>[:<tag>]`
	- 【別名イメージ作成】 `docker tag <old_image> <new_image>[:<new_tag>]`
	- 【イメージ削除】 `docker rmi [opiton] <image1> <image2> ...`
- conteiner の操作
	- 【コンテナ一覧表示】 `docker ps [<option>]`
		- `-a` ：停止中コンテナも含む（ない場合は稼働中コンテナのみ）
	- 【コンテナ作成】 `docker create [<option>] <image>[:<tag>] [<command>]`
	- 【コンテナ起動】 `docker start [<option>] <container> [<container> ...]`
	- 【コンテナ停止】 `docker stop <container> [<container> ...]`
	- 【コンテナ再起動】 `docker restart <container>`
	- 【コンテナ作成＆起動】 `docker run [<option>] <image>[:<tag>] [<command>]`
		- `-d` (`--detach`) ：コンテナを生成し、バックグラウンドで実行する。
		- `-i` (`--interactive`) ：コンテナの標準入力を開く。
		- `-t` (`--tty`) ：端末デバイスを使う。
		- `--name <container>` ：コンテナに名前をつける（指定しない場合は、自動で付与される）
		- `--rm` ：コンテナ実行完了後にコンテナを自動で削除する。（削除条件：exit でコンテナから抜けた、stop でコンテナを停止した）
		- `-u <user_name>` (`--user`) ：ユーザー名または UID を指定する。
		- `--add-host=<host_name>:<ip_address>` ：コンテナの /etc/hosts にホスト名とIPアドレスを定義する。
		- `-h` (`--hostname`) ：コンテナ自身のホスト名を指定する。
		- `-p <host_port>:<container port>` (`--publish`) ：ホストとコンテナのポートマッピング。
		- `-e <env_var>` (`--env`) ：環境変数を設定する。
		- `-v <host_dir>:<container_dir>` (`--volume`) ：コンテナにホストのディレクトリをマウントする
		- `-w=<dir_path>` (`--workdir`) ：コンテナの作業ディレクトリを指定する
	- 【コンテナ接続（PID=1プロセス）】 `docker attach [<option>] <container>`
	- 【コンテナ接続（新規プロセス起動）】 `docker exec [<option>] <container> <command>`
	- 【稼働コンテナ状況確認】 `docker status <container>`
	- 【稼働コンテナプロセス確認】 `docker top <container>`
	- 【コンテナ削除】 `docker rm <container>`
- image の保存と再構築
	- 【イメージ作成（from Dockerfile）】 `docker build -t <image>[:<tag>] <ockerfile_path>`
	- 【イメージ作成（from コンテナ）】 `docker commit <container> <image>`

## Tips

- [docker.ioとdocker-ceの違い](https://scrapbox.io/nabe-yu/docker.io%E3%81%A8docker-ce%E3%81%AE%E9%81%95%E3%81%84)
	- docker-ce：本家が提供するdocker-engine
		- ce＝コミュニティエディション
		- ee＝エンタープライズエディション
	- docker.io：Ubuntuが提供するdocker-engine
		- docker.ioはバージョンが本家に比べて古いことがあるので、  
		最新版を使いたければdocker-ceをインストールすることをお勧めする。
- [attach と execの違い](https://www.wantanblog.com/entry/2020/03/10/223050)
	- `attach`
		- 「PID=1」で起動しているプロセスに接続する。  
		- exitコマンドでシェルを終了するとコンテナが停止する。
	- `exec`
		- プロセスを新たに生成して接続する。（/bin/bash 等）
		- exitコマンドでシェルを終了するとコンテナが停止しない。
-  Docker デーモンが起動しないエラーについて
	- 事象：WSL2へインストールした直後のDocker コマンド実行時に、以下のエラーが発生してDockerコマンドを実行できないことがある。

		```shell
		Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
		```

	- 対処法：dockerグループへ参加してWSL2を再起動する。

		```shell
		sudo usermod -aG docker $USER
		wsl --shutdown
		```

[トップに戻る](../index.md)
