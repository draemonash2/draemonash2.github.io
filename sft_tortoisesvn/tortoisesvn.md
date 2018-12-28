[トップに戻る](../index.md)

# ToDo
- コミットの取り消し（コミットログに残さない）

# コマンド
- 【ローカルリビジョン番号一覧】svn ls -Rv .
- 【リビジョン間の変更ファイル一覧】svn diff -r 3:head --summarize
- 【特定ディレクトリ配下の更新を無視】svn update --set-depth exclude [path]
	- 対象のディレクトリが消えて、以降の更新操作ではそのディレクトリは一切無視される。
- 【特定ディレクトリ配下の更新を無視を元に戻す】svn update --set-depth infinity

[トップに戻る](../index.md)
