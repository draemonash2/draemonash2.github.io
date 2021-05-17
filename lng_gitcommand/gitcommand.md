[トップに戻る](../index.md)

# 構文

- 【ログ表示】git log
- 【ログ表示(2件のみ)】git log -2
- 【ログ表示(1行表示)】git log --oneline
- 【ログ表示(グラフ表示)】git log --graph
- 【ディレクトリ作成】git init
- 【状態確認】git status

- 【クローン】git clone https://github.com/draemonash2/codes.git codes
- 【プッシュ】git push
- 【プル】git pull
- 【[フェッチ(取得)](#fetch)】git fecth #→リモートの「master」ブランチ → ローカルの「origin/master」ブランチ
- 【フェッチ後のマージ】git merge #→ローカルの「origin/master」ブランチ → ローカルの「master」ブランチ

- 【リモートリポジトリ作成】git remote add origin URL
- 【リモートリポジトリ紐づけ確認】git remote #→originになっていれば完了
- 【リモートリポジトリ紐づけ削除】git rm origin
- 【初回プッシュ】git push --set-upstream origin master #→ローカルブランチリモート反映
- 【初回プル】git pull origin ブランチ名 #→リモートリポジトリブランチローカル反映

- 【ブランチ作成】git checkout -b ブランチ名
- 【ブランチ切替】git checkout ブランチ名
- 【ブランチ削除】git branch -d ブランチ名
- 【ブランチ一覧表示】git branch
- 【スタッシュ(変更データ仮置き)】git stash

- ローカルリポジトリ操作
	- 【コミット 追加】git commit -m “命令形メッセージ”
	- 【コミット 上書き】git commit --amend
		- 英単語amend＝修正する
	- 【コミット 内容追加】git commit --amend --no-edit #→前回のコミットメッセージのまま
	- 【コミットコメント修正】git commit --amend -m "修正されたコミット"

- インデックス 作業ツリー操作
	- 【追加】git add filename.txt
	- 【追加(全て)】git add -A
	- 【ファイル削除】git rm file.txt
	- 【特定コミットへ作業ツリー巻戻し】git checkout ハッシュ値
	- 【リネーム】git mv 旧ファイル名 新ファイル名

- [変更取消し](https://www-creators.com/archives/1290)
	- 【変更取消し 作業ツリーのみ】git checkout ファイル名
	- 【変更取消し 作業ツリー＋インデックス】git reset HEAD ファイル名
	- 【変更取消し コミット後1】git revert HEAD #→変更を打ち消すコミットを作成
	- 【変更取消し コミット後2】git reset HEAD #→直前のコミットを消去する
	- 【変更取消し コミット後2】git reset HEAD #→直前のコミットを消去する
	- 【変更取消し プッシュ後1】git reset --hard ハッシュ値
	- 【変更取消し プッシュ後2】git reset --hard HEAD^ #→直前コミット消去
	- 【直前reset取消し】git reset --hard ORIG\_HEAD
	- 【全変更取消し インデックス変更後】git checkout -f
	- 【ファイル変更削除】git checkout -- ファイル名
	- [★](https://www-creators.com/archives/1290)

- 変更差分表示
	- 【変更差分表示 作業ツリー⇔インデックス間】git diff
	- 【変更差分表示 作業ツリー⇔LocalRepo(HEAD)間】git diff HEAD
	- 【変更差分表示 インデックス⇔LocalRepo(HEAD)間】git diff --cached
	- 【変更差分表示 ローカル⇔リモート】git diff HEAD..リモート名/ブランチ名
	- 【変更差分表示 ローカルファイルvs直前コミット】git diff -- ファイルパスA
	- 【変更差分表示 ローカルファイル間】git diff -- ファイルパスA
	- 【変更差分表示】git log -p ファイル名
		- ★diffと何が違う？

- マージ
	- 【マージ(Non Fast-Forward)】git merge [--no-ff] ブランチ名 #→ 今のブランチに選択したブランチをマージ
	- 【マージ(Fast-Forward)】git merge --ff ブランチ名
	- 【マージ取り消し】git revert -m 1 ハッシュ値
	- 【リベース】git rebase master #→最新のマスターをブランチに反映させるために使う
	- 【コミット編集】git rebase -i #→入力後、エディタが立ち上がり、以下のコマンドでコミットを編集する
		- pick：コミットをそのまま使う。内容を変更しない。
		- reword：コミットメッセージを変更する。コミット内容は変更しない。
		- edit：コミットを修正する。
		- squash：ひとつ前のコミットにまとめる。コミットメッセージを書き直す。
		- fixup：ひとつ前のコミットにまとめる。コミットメッセージをそのまま使う。
		- exec：shell でコマンドを実行する
	- 【リベース中断】git rebase --abort
	- 【[特定コミット取込み(コミットする)](#cherry-pick)】git cherry-pick ハッシュ値
	- 【特定コミット取込み(コミットしない)】git cherry-pick -n ハッシュ値

- [スタッシュ](#stash)
	- 【スタッシュ 保存1】git stash #→untracked fileを含めない
	- 【スタッシュ 保存2】git stash -u #→untracked fileも含める
	- 【スタッシュ 保存(メッセージ付き)】git stash save "message" #→現在の作業を一時的に退避する
	- 【スタッシュ 復元1】git stash pop #→退避した作業を復元する(スタッシュ削除)
	- 【スタッシュ 復元2】git stash apply #→退避した作業を復元する(スタッシュ保持)
	- 【スタッシュ 一覧表示】git stash list
	- 【スタッシュ 削除(最新分)】git stash drop
	- 【スタッシュ 削除(番号指定)】git stash drop stash@{1}
	- 【スタッシュ 全削除】git stash clear

- 【github上から指定ファイル完全消去】 `find . -name .ファイル前 -print0 | xargs -0 git rm`
	- github上でrevertした場合は必ずプルリクエストまで出す


[トップに戻る](../index.md)
