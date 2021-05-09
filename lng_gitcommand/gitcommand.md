[トップに戻る](../index.md)

# 構文
- 【クローン】git clone https://github.com/draemonash2/codes.git codes

- 【ディレクトリ作成】git init
- 【追加】git add filename.txt
- 【追加(全て)】git add -A
- 【状態確認】git status

- 【リモートリポジトリ作成】git remote add origin URL
- 【リモートリポジトリ紐づけ確認】git remote #→originになっていれば完了
- 【リモートリポジトリ紐づけ削除】git rm origin
- 【ローカルブランチリモート反映(最初のプッシュ)】git push --set-upstream origin master
- 【リモートリポジトリブランチローカル反映(最初のプル)】git pull origin ブランチ名

- 【コミット】git commit -m “命令形メッセージ” ()
- 【ログ表示】git log
- 【変更取り消し(履歴を残す安全な方法)】git revert
- 【変更取り消し(コミット取消＆過去の状態に戻る)】git reset ファイル名
- 【★コミットを指定して戻る】git reset --hard ハッシュ値

- 【プッシュ】git push
- 【プル】git pull
- 【フェッチ】git fecth

- 【マージ】git merge ブランチ名 #→ 今のブランチに選択したブランチをマージ
- 【マージ取り消し】git revert -m 1 マージ番号

- 【変更を強制的に上書きして元に戻す(マスターブランチで作業してしまった時使用)】git checkout -f
- 【ブランチ作成】git checkout -b ブランチ名
- 【ブランチを変更】git checkout ブランチ名
- 【ファイルの変更を削除】git checkout -- ファイル名
- 【ブランチ削除】git branch -d ブランチ名
- 【ブランチ一覧表示】git branch
- 【スタッシュ(変更データ仮置き)】git stash
- 【リベース(最新のマスターをブランチに反映させるために使う)】git rebase maste

- 【github上から指定ファイル完全消去】find . -name .ファイル前 -print0 | xargs -0 git rm
	- github上でrevertした場合は必ずプルリクエストまで出す

[トップに戻る](../index.md)
