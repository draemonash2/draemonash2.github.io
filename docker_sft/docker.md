
# Docker

[トップに戻る](../index.md)

## インストール手順

[Docker ドキュメント](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository) のインストール手順に従い、docker-ceをインストールする。  
なお、WSL2 へのインストール手順は、ネイティブLinuxへのインストール手順と同じで問題ない。

## Tips

- [docker.ioとdocker-ceの違い](https://scrapbox.io/nabe-yu/docker.io%E3%81%A8docker-ce%E3%81%AE%E9%81%95%E3%81%84)
	- docker-ce：本家が提供するdocker-engine
		- ce＝コミュニティエディション
		- ee＝エンタープライズエディション
	- docker.io：Ubuntuが提供するdocker-engine
		- docker.ioはバージョンが本家に比べて古いことがあるので、  
		最新版を使いたければdocker-ceをインストールすることをお勧めする。
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
