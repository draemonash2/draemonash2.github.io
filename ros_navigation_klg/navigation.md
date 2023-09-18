
# navigation

[トップに戻る](../index.md)

## 疑問

- [目標地点ってどうやって与えるの？](https://robo-marc.github.io/navigation_documents/navigation_overview.html)
	- → [geometry_msgs/PoseStampedを使うっポイ](https://daily-tech.hatenablog.com/entry/2017/02/10/074925)
- [costmap](https://qiita.com/srs/items/fba2c83b96d17b2680e6)とは？
	- 空間中の通れそうな領域、障害物のある領域を数値で表現した地図のこと [[1]](https://qiita.com/ledmonster/items/8fbc9f7ea060a75e9018#%E3%82%B3%E3%82%B9%E3%83%88%E3%83%9E%E3%83%83%E3%83%97%E3%81%A3%E3%81%A6%E4%BD%95)
- ★[plugin システム](https://qiita.com/ledmonster/items/8fbc9f7ea060a75e9018#global-costmap-%E3%82%84-local-costmap) pluginlib とは？

## 用語

- [amcl (Adaptive Monte Carlo localization)](https://rtc-fukushima.jp/technical/6309/)
	- 2Dで移動するロボットのための確率的な位置推定システム。  
	パーティクルフィルタ（またはKLDサンプリング）を使用したモンテカルロ法を用いて、既知のマップに対するロボットの姿勢の追跡を行います。[[1]](https://robo-marc.github.io/navigation_documents/amcl.html)
	- navigation stackは、「map_server」で既存地図の配信を行い、「amcl」でパーティクルフィルタによる自己位置推定をし、「move_base」でナビゲーションタスクを実行する。[[1]](https://rtc-fukushima.jp/technical/6309/)
	- 既存の地図とパターンマッチングを行って自己位置を推定するパッケージ。[[1]](https://qiita.com/srs/items/b07a22425548c41bfd04#%E6%A6%82%E8%A6%81)
- gmapping
	- SLAM（地図作成＋自己位置推定）を行うパッケージ。[[1]](https://qiita.com/srs/items/b07a22425548c41bfd04#%E6%A6%82%E8%A6%81)

[トップに戻る](../index.md)
