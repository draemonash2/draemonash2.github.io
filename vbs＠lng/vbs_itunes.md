[トップに戻る](../index.md)

# ライブラリ
 https://github.com/draemonash2/codes/blob/master/vbs/lib/iTunes.vbs

# API Reference
[iTunes COM Interface Documentation v8.1.0.52](http://www.joshkunz.com/iTunesControl/main.html)

# Tips
- トラック名はユニークではないため、同トラック名のファイルが複数あるトラックに対して以下のような指定をした場合、先にヒットしたトラックを再生する。そのため、この方法では前者以外のトラックは再生できない。
	- objTracks.ItemByName( "Best Friend" ).Play
	- Persistent ID はユニークな ID。「iTunes Music Library.xml」から抜き出してきてもよいかも。
		- objTracks.ItemByPersistentID( "618E2B28", "23B253BC" ).Play

# 構文
## 「～」は改行を示す。
- 【iTunesObject 取得】Set objItunes = WScript.CreateObject("iTunes.Application")
	- 【ライブラリ XML パス取得】objItunes.LibraryXMLPath
	- 【プレイリストオブジェクト取得】Set objPlayList = objItunes.Sources.Item(1).Playlists.ItemByName("ミュージック") '音楽（ローカルに保存したファイル＋購入したファイル）の一覧を取得
	- 【ファイル登録】objPlayList.LibraryPlaylist.AddFile( "c:\music" )

- 【ファイルパスからトラックを特定】
	```vb
	sTrgtTrackName = "Best Friend"
	sTrgtTrackPath = "Z:\300_Musics\100_J-Pop\Artist\$ Other\Best Friend.mp3"
	
	Set objItunes = WScript.CreateObject("iTunes.Application")
	Set objPlayList = objItunes.Sources.Item(1).Playlists.ItemByName("ミュージック")
	Set objSearchResult = objPlayList.Search( sTrgtTrackName, 5 )
	For lHitIdx = 1 to objSearchResult.Count
		With objSearchResult.Item(lHitIdx)
			If .Location = sTrgtTrackPath Then
				.Genre = "J-Pop"
				Exit For
			Else
				'Do Nothing
			End If
		End With
	Next
	```

- 【トラック属性メンバ】
	``` vb
	MsgBox .Kind
	MsgBox .Playlist
	MsgBox .Album
	MsgBox .Album
	MsgBox .Artist
	MsgBox .BitRate
	MsgBox .BPM
	MsgBox .Comment
	MsgBox .Compilation
	MsgBox .Composer
	MsgBox .DateAdded
	MsgBox .DiscCount
	MsgBox .DiscNumber
	MsgBox .Duration
	MsgBox .Enabled
	MsgBox .EQ
	MsgBox .Finish
	MsgBox .Genre
	MsgBox .Grouping
	MsgBox .KindAsString
	MsgBox .ModificationDate
	MsgBox .PlayedCount
	MsgBox .PlayedDate
	MsgBox .PlayOrderIndex
	MsgBox .Rating
	MsgBox .SampleRate
	MsgBox .Size
	MsgBox .Start
	MsgBox .Time
	MsgBox .TrackCount
	MsgBox .TrackNumber
	MsgBox .VolumeAdjustment
	MsgBox .Year
	MsgBox .Artwork
	```

[トップに戻る](../index.md)
