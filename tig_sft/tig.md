[トップに戻る](../index.md)

# コマンド

- ビュー
	- 【デフォルト】 `m` # main (git tree)
	- 【作業ディレクトリ、ステージング済みのファイル表示】 `s` # status
	- 【branch/tag一覧】 `r` # refs
	- 【commit間のファイル差分表示】 `d` # diff
	- 【ログ表示】 `l` # log
	- 【grep】 `g` # grep
	- 【ディレクトリツリー】 `t` # tree
	- 【blame】 `b` # blame
	- 【ヘルプ】 `h` # help

- 【git add】 `s -> 選択 -> u`
- 【git commit】 `s -> c -> コミットメッセージ入力`
- 【git checkout】 `r -> 選択 -> c`

# Tips

-  [blameビューで,を押すと、カーソルが指しているコミットの前の時点のblameが見れる](https://qiita.com/vivid_muimui/items/7e7a740e6537749de0c0#blame%E3%82%92%E5%86%8D%E5%B8%B0%E7%9A%84%E3%81%AB-)
-  [statusやtreeビューででファイルの上にカーソルがある状態でeを押すとエディターが立ち上がる](https://qiita.com/vivid_muimui/items/7e7a740e6537749de0c0#%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%AE%E7%B7%A8%E9%9B%86-e)

# カスタマイズ
- [カスタマイズ方法](https://qiita.com/vivid_muimui/items/7e7a740e6537749de0c0#%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%9E%E3%82%A4%E3%82%BA)
- カスタマイズ例
```
set vertical-split = false														# サブビューを横分割にする
set main-view = id date author commit-title:graph=yes,refs=yes					# main viewの左端にコミットIDを表示する
set diff-context = 4															# 差分の前後の表示行数（diff-context)を指定
set author-width = 14
set filename-width = 16
set id-width = 14
set blame-options = -C -C -C
set line-graphics = ascii
set line-number-interval = 5
set horizontal-scroll = 33%
set read-git-colors = no
set show-author = abbreviated
set show-filename = always
set show-date = local
set show-notes = yes
set show-refs = yes
set show-id = yes
set show-rev-graph = yes
set show-changes = yes
set vertical-split = yes
set split-view-height = 70%
set status-untracked-dirs = yes
set tab-size = 2
set diff-context = 1
set ignore-space = some
set commit-order = topo
set ignore-case = no
set wrap-lines = no
set focus-child = yes
set show-line-numbers = yes

color default white black
color cursor default magenta
color date cyan default
color delimiter cyan default
color line-number yellow default
color diff-header yellow default
color diff-index blue default
color diff-chunk magenta default
color "Reported-by:" green default
color graph-commit cyan default
 
bind generic W :!git reflog														# reflogをpagerで表示
bind generic y @sh -c "echo %(commit) | pbcopy"									# commitハッシュをコピー
bind generic ^ @hub browse														# リポジトリのGitHubを表示
bind generic F none
bind generic F !git fetch
bind generic M none
bind main B ?git checkout -b "%(prompt Enter new branch name: )"				# checkout -b
bind main U ?git poh "%(prompt Enter push branch => )"							# poh = push origin HEAD:$1
bind main <Ctrl-r> ?git rebase -i %(commit)										# rebase
bind branch B ?git checkout -b "%(prompt Enter new branch name:)" %(branch)		# checkout -b
bind branch [ @hub compare %(branch)											# 選択したbranchのcompare画面
bind branch n !git checkout -b %(prompt) %(branch)
bind branch P !git push origin %(branch)
bind branch L !git pull origin %(branch)
bind branch M none
bind branch M !git merge %(branch)
bind status <Ctrl-r> ?git reset --hard HEAD										# reset hard
```

[トップに戻る](../index.md)
