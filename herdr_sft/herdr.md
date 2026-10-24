
# Herdr

[トップに戻る](../index.md)

## コマンド＆ショートカットキー（デフォルト）

- 【サイドバー表示/非表示】 `Prefix + b`

## Tips

- Tmuxにある以下の機能は2026/10時点で存在しない。
    - 全ペインに同時に入力 `prefix -> shift+b`
- Dockerコンテナを跨ぐ状態監視について
    - 通常、ホスト環境上のHerdrは、Dockerコンテナ上のclaudeの状態を監視できない。  
    そのため、以下のようにDockerコンテナ上のclaudeを直接起動することで対処できる。

## トラブルシューティング

- Dockerコンテナを跨ぐ状態監視ができない
    - 事象
        - 通常、ホスト環境上のHerdrは、Dockerコンテナ上のclaudeの状態を監視できない。  
    - 対策
        - 以下のようにDockerコンテナ上のclaudeを直接起動する。

            ```sh
            HERDR_AGENT=claude exec docker exec -e DISPLAY -e TERM -e COLORTERM -it $CONTAINER_NAME /ros_entrypoint.sh /home/$USER/.local/bin/claude "$@"
            ```

[トップに戻る](../index.md)
