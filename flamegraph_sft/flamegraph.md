[トップに戻る](../index.md)

# インストール方法

1. perf インストール
    ```shell
    sudo apt install linux-tools-$(uname -r) linux-tools-generic
    ```
1. flamegraphダウンロード(格納先は任意)
   - https://github.com/brendangregg/FlameGraph

# 実行方法

1. 可視化対象のプログラム起動
1. 以下コマンド実行により、計測開始
    ``` shell
    $ cd <flamegraph_dir>
    $ perf record -F 99 -p <PID> -g --call-graph dwarf
    ```
1. 可視化対象プログラム実行
1. 可視化対象プログラム終了後、perfコマンドをctrl+cで終了
1. svgファイル出力
    ``` shell
    $ cd <flamegraph_dir>
    $ perf script | ./stackcollapse-perf.pl > out.perf-folded
    $ ./flamegraph.pl out.perf-folded > perf.svg
    ```

[トップに戻る](../index.md)
