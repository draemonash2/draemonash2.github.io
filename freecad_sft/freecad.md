[トップに戻る](../index.md)

# FreeCAD

## インストール方法

TODO:

## Tips

- FreeCAD軽量化方法
    1. 3Dビュー更新を停止する
        `View` -> `表示をフリーズ` -> `ビューをフリーズ`
- コマンドライン実行方法
    - CUIプログラム

        ```shell
        freecadcmd script.py -- --opt1 0.1 --opt2 2 -r
        ```

        - TODO: 引数を捨てる必要がある。
        - AppImage版FreeCADの場合はこのコマンドは使えない。
    - GUIプログラム

        ```shell
        freecad -c script.py
        ```

        - AppImage版FreeCADの場合は`freecad`をAppImageファイルパスに置き換える（例: `/path/to/FreeCAD.AppImage`）
        - TODO: 引数がある場合の実行方法確認
- Partオブジェクトの移動方法
    -  ドラフトワークベンチ上で移動する

[トップに戻る](../index.md)
