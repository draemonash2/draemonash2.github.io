[トップに戻る](../index.md)

# 構文
- コピーコンストラクタ
	- `Human::Human(const Human& human) `
		- *でないことに注意！

# 用語
- アクセスチェック
	- ★
- 純粋仮想関数
	- クラス宣言時は実装がない関数。サブクラスにて実装する場合に使う。
- 仮想関数
	- 基底クラスのメンバ関数ではなく、サブクラスのメンバ関数を呼び出したい場合に使う。
- protected継承
	- 基底クラスのpublicをprotectedに変更して継承する
- private継承
	- 基底クラスのpublicをprivateに変更して継承する
- auto
	- 型推論を行うようにするためのデータ型（C++11にて追加）
	[詳細はこちら](https://uchan.hateblo.jp/entry/2019/02/22/105622)
- namespace（名前空間）
	- 名前の衝突を防ぐために必要なもの
		- [詳細はこちら](https://qiita.com/_EnumHack/items/430da105a541f9ecd774)
		- [こちらも](http://wisdom.sakura.ne.jp/programming/cpp/cpp38.html)
	- 名前空間に別名をつけることも可能
		- [namespaceの短縮（エイリアス）](https://qiita.com/_EnumHack/items/430da105a541f9ecd774)
- using キーワード
	- いちいち名前空間で修飾するのは面倒な時に使う
		- `using namespace std;`
	- 名前空間内の変数や関数を個別に指定する場合に使う
		- `using aaa::show; //ここから後に記述されるshowは、aaa::showと認識される。`
- UDLs（User Defined Literals）

# Tips
- char型をcoutすると、数値が出力されない
	- 例
``` c++
char a = 2;
cout << a << endl;
```
	- 原因
		- char型をcoutする場合、数値をASCIIコードとしてみなして出力する（数値が65の場合は'A'を出力する）
		ASCIIコードの2は制御文字のため、出力されない
- サブクラスの定義時、基底クラスのコンストラクタおよびデコンストラクタも呼び出される。
	- [詳細はこちら参照](https://yttm-work.jp/lang/cpp/cpp_0006.html#head_line_04)
- クラス定義時にスコープを指定しない場合、publicになる？
	- デフォルトで、メンバはprivateアクセス修飾子を持つ
- stringクラスのclearは空文字代入と何が違う？
	- 違いはない（空文字代入でも空になる）が、クリアする目的であることを明示できるメリットはある。
- friendって使う？
	- 使わない。適切に OOAD (Object-Oriented Analysis and Design) ができていればまず使うことは無い/使う必要が無い。(詳細はこちら)[https://ja.stackoverflow.com/questions/44299/c-friend%E9%96%A2%E6%95%B0%E3%81%A8friend%E3%82%AF%E3%83%A9%E3%82%B9%E3%81%AE%E9%81%95%E3%81%84%E3%82%92%E7%9F%A5%E3%82%8A%E3%81%9F%E3%81%84%E3%81%A7%E3%81%99]

[トップに戻る](../index.md)
