[トップに戻る](../index.md)

# subversion cui インストーラー
> http://subversion.tigris.org/servlets/ProjectDocumentList?folderID=11151&expandFolder=11151&folderID=91

# 構文
- 【コミット】svn commit <PATH> -m "<MESSAGE>"

- 【追加】svn add <PATH>
- 【削除】svn delete <PATH>

- 【チェックアウト（配下のファイル、フォルダ全て）】svn checkout <URL> <PATH>
	- 例）svn checkout file:///C:/svn\_repo/c/FreeRTOSV7.1.1/Source/portable/IAR C:\Users\draem\_000\Desktop\IAR
- 【チェックアウト（直下のファイルのみ）①】svn checkout --non-recursive <URL> <PATH>
	- 例）svn checkout --non-recursive file:///C:/svn\_repo/c/FreeRTOSV7.1.1/Source/portable/IAR C:\Users\draem\_000\Desktop\IAR4
- 【チェックアウト（直下のファイルのみ）②】svn checkout --depth=files <URL> <PATH>
	- 例）svn checkout --depth=files file:///C:/svn\_repo/c/FreeRTOSV7.1.1/Source/portable/IAR C:\Users\draem\_000\Desktop\IAR2
- 【チェックアウト（直下のファイル、フォルダのみ）】svn checkout --depth=immediates <URL> <PATH>
	- 例）svn checkout --depth=immediates file:///C:/svn\_repo/c/FreeRTOSV7.1.1/Source/portable/IAR C:\Users\draem\_000\Desktop\IAR3

- 【エクスポート】svn export <URL> <PATH>
	- オプションはチェックアウトコマンドと同じ
	
- 【ローカルリビジョン番号一覧】svn ls -Rv .
- 【リビジョン間の変更ファイル一覧】svn diff -r 3:head --summarize
- 【特定ディレクトリ配下の更新を無視】svn update --set-depth exclude [path]
	- 対象のディレクトリが消えて、以降の更新操作ではそのディレクトリは一切無視される。
- 【特定ディレクトリ配下の更新を無視を元に戻す】svn update --set-depth infinity

[トップに戻る](../index.md)
