[トップに戻る](../index.md)

# 用語
- コピーコンストラクタ
	- `Human::Human(const Human& human) `
		- *でないことに注意！
- アクセスチェック
	- ★
- 仮想関数
	- 基底クラスのメンバ関数ではなく、サブクラスのメンバ関数を呼び出したい場合に使う。
	- e.g. `virtual void speak();`
- 純粋仮想関数
	- クラス宣言時は実装がない関数。サブクラスにて実装する場合に使う。
	- 純粋仮想関数を持つクラスはインスタンス生成できない。左記の理由で、純粋仮想関数を持つクラスは抽象クラスともいわれる。
	- e.g. `virtual void speak() = 0;`
- auto
	- 型推論を行うようにするためのデータ型（C++11にて追加）[詳細はこちら](https://uchan.hateblo.jp/entry/2019/02/22/105622)
	- 型指定が複雑なもの（複雑なポインタやイテレータ、ラムダ式等）は、autoで簡略化できる。
- フレンド関数
	- クラス定義時にfriendをつけた関数は、関数内で左記クラス内のメンバにアクセスできるようになる。
- 継承時のアクセス指定子
	- public
		- 基底クラスと同じアクセス範囲のまま継承する
	- protected
		- 基底クラスのpublicをprotectedに変更して継承する
	- private
		- 基底クラスのpublicをprivateに変更して継承する
- namespace（名前空間）
	- 名前の衝突を防ぐために必要なもの
		- [詳細はこちら](https://qiita.com/_EnumHack/items/430da105a541f9ecd774)
		- [こちらも](http://wisdom.sakura.ne.jp/programming/cpp/cpp38.html)
	- 名前空間に別名をつけることも可能
		- [namespaceの短縮（エイリアス）](https://qiita.com/_EnumHack/items/430da105a541f9ecd774)
- usingの種類
	- using宣言(別名)
		- 型に別の名前を与える
			- e.g. `using integer = int;`
		- ちなみに、namespaceでも同じことをできる。
			- e.g. `namespace sub = module::submodule;`
	- using宣言(省略)
		- 名前空間内の変数や関数を個別に指定する場合に使う
			- e.g. `using aaa::show; //ここから後に記述されるshowは、aaa::showと認識される。`
	- usingディレクティブ
		- コンパイラーに対して特定の名前空間の省略を指示することができる
			- e.g. `using namespace module;`
- UDLs（User Defined Literals）
	- 和訳：ユーザー定義リテラル
	- "hello"といったリテラルに対して付けられるサフィックスをオーバーロードできるようにすることで、ユーザーがリテラルに意味を持たせられるようにする機能
- キャストの種類
	- static\_cast
		- 暗黙の型変換ができる時だけキャストする。不正な変換(intをint\*に変換)の場合はコンパイルエラーが発生する。
		- 必要ならば値を変えることができるらしい（[詳細はこちら](https://cpplover.blogspot.com/2010/07/c.html)）
	- const\_cast
		- const 修飾付きの型のconstだけを除去する。
	- reinterpret\_cast
		- static\_castでは変換できない型を強制的にキャストする。
		- ポインタ同士のように互いに関連性がありそうならばキャストする。
			- C言語のキャストとは微妙に違うみたい…
	- dynamic\_cast
		- 実行時にキャストできるか確認する。
		- 基本型のポインターを派生型のポインターに変換する時に使うキャスト。
			- 基本的に使われないもの。
				- 理由は、そもそも抽象クラスのオブジェクトを具象クラスのオブジェクトを入れるダウンキャスト自体がよくないため！[詳細はこちら](http://yohshiy.blog.fc2.com/blog-entry-15.html)
- [糖衣構文](https://ja.wikipedia.org/wiki/%E7%B3%96%E8%A1%A3%E6%A7%8B%E6%96%87)
	- 読み書きのしやすさのために導入される書き方。
	- 複雑でわかりにくい書き方と全く同じ意味になるものを、よりシンプルでわかりやすい書き方で書くことができる書き方。
- [ラムダ式](https://qiita.com/rita0222/items/bd895e82251d56917736)
	- 関数オブジェクトを簡単に定義できるようにするもの。
- STL（Standard Template Library）の種類
	- ★
	- [vector](https://bi.biopapyrus.jp/cpp/syntax/vector.html)
		- 配列を拡張したクラスで、あらかじめサイズを指定しなくても利用できるようにしたクラス。
		- メンバ関数：push\_back、clear、size、empty等
	- [list](https://bi.biopapyrus.jp/cpp/syntax/vector.html)
		- 配列を拡張したクラスで、任意の位置に要素を挿入したり、任意の位置の要素を削除したりすることを想定して作られている。
		- メンバ関数…push\_front、push\_back、insert等
	- map
	- queue
	- stack
-  [ADL（Argument Dependent Look-up）](https://qiita.com/amowwee/items/dd9d75d56af2562dcbbd)
	- 「実引数依存の名前検索」のこと。ある型のオブジェクトが関数呼出の際に実引数として用いられると、関連するネームスペースからも、その関数が探索されるという仕様。
- コピーの種類
	- シャロ―コピー（浅いコピー）
		- データの実体を指し示すポインタだけがコピーされて、データの実体がコピーされないこと
	- ディープコピー（深いコピー）
		- データの実体もコピーすること
- MBCS（Multi Byte Character Set）
	- charでは収まらない文字には複数の charの組に 1 文字を割り当てる
	- 例：UTF-8、Shift\_JIS
	- C++ で MBCS を扱うクラスが std::string
- WCS（Wide Character Set）
	- charより大きなサイズの型 wchar\_tを用意して、wchar\_tの列で文字列を表す。(＝ワイド文字列)
	- 例：UTF-16(世界中のあらゆる文字に一意のコードを割り当てる)
	- C++ で WCS を扱うクラスが std::wstring
- [プレースホルダ](https://elsammit-beginnerblg.hatenablog.com/entry/2021/07/25/150918)
	- 正式な値が入るまで一時的に場所を確保しておく方法のこと
	- プレースホルダ（ placeholder） は、「 置き換え られる もの」 という 意味
	- テンプレートパラメーターのことを指すことがある？
- [関数オブジェクト](https://ja.wikipedia.org/wiki/%E9%96%A2%E6%95%B0%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88)
	- 関数（サブルーチンないしプロシージャ）を、オブジェクトとしたもの
- [ファンクタ](https://marycore.jp/prog/cpp/function-object/)
	- クラスのoperator()演算子を多重定義／オーバロードすることで、クラスのインスタンスに対して関数と同等の振る舞いをさせることができます。
	- このような関数オブジェクトはファンクタ（functor）と呼ばれています。
	- ()演算子をオーバーロードした関数オブジェクトのこと
- 集約(aggregate)と委譲(delegate)
	- ★
- [SFINAE（Substitution Failure Is Not An Error）](https://cpprefjp.github.io/lang/cpp11/sfinae_expressions.html)
	- テンプレートの置き換えに失敗した際に、即時にコンパイルエラーとはせず、置き換えに失敗した関数をオーバーロード解決の候補から除外するという言語機能
	- スフィネェと読む
- [RAII（Resource Acquisition Is Initialization）](https://ja.wikipedia.org/wiki/RAII)
	- 資源（リソース）の確保と解放を、クラス型の変数の初期化と破棄処理に結び付けるというプログラミングのテクニック
	- 基本的な活用例は、動的確保されたメモリを自動解放するスマートポインタ (smart pointer) である。
- NSDMI（Non Static Data Member Initializer）
	- 和訳：非静的メンバー変数の初期化子
	- メンバー変数のデフォルト値を指定すること
- RTTI（RunTime Type Information）
	- 実行時型情報
	- コンパイル時ではなく実行時に、そのオブジェクトの型について調べる機能
- NTTP（Non-Type Template Parameter）
	- 型ではなくコンパイル時に扱える値に指定されたテンプレートパラメーターのこと
	- `template <int i>`
- NTCTS（Null Terminated Character Type String）
	- 和名：ヌル終端文字列
	- ヌル文字で終端された文字列のこと
- ジェネリックラムダ
	- パラメータにテンプレートを使用できるようにした機能
- [Two-phase name look up](https://mimosa-pudica.net/cpp-specialization.html)
	- テンプレート内で使われる名前について、 (0)テンプレートパラメータに依存しない名前は（通常通り）定義された時点で探索を行い、 (1)テンプレートパラメータに依存する名前はテンプレートが実体化される時点で探索を行う、というもの。
- [クロージャ](https://e-words.jp/w/%E3%82%AF%E3%83%AD%E3%83%BC%E3%82%B8%E3%83%A3.html)
	- あるコードブロック内で定義された関数などが、そのブロックをスコープとする変数などを参照できること。また、そのような機能を利用してブロック内部で定義された関数のこと。
	- 目的はオブジェクト内部で使用している変数やメソッドを他人が容易に変更できないようにする(＝カプセル化)
- [右辺値](http://yohshiy.blog.fc2.com/blog-entry-335.html)
	- 使用する式を超えて保持されない一時的な値（≠代入式の右辺にある値）
	- 右辺値参照…もう使わなくなるオブジェクトの参照

# Tips
- char型をcoutすると、数値が出力されない
	- 例
``` c++
char a = 2;
cout << a << endl;
```
	- 原因
		- char型をcoutする場合、数値をASCIIコードとしてみなして出力する（数値が65の場合は'A'を出力する）。ASCIIコードの2は制御文字のため、出力されない。
- サブクラスの定義時、基底クラスのコンストラクタおよびデコンストラクタも呼び出される。
	- [詳細はこちら参照](https://yttm-work.jp/lang/cpp/cpp_0006.html#head_line_04)
- クラス定義時にスコープを指定しない場合、publicになる？
	- デフォルトで、メンバはprivateアクセス修飾子を持つ
- クラステンプレート使用時は、コンストラクタの引数が必要？(引数なしで定義すると、コンパイルエラーが発生する)
	- いらない。インスタンス生成時に<>で型を指定する。
- クラステンプレート使用時は、クラス定義内に関数の処理を実装する必要がある？
	- クラス定義内に実装しなくてもできるけど、いろいろテクニックがいるらしい。[詳細はこちら](https://blog.amagi.dev/entry/2013/12/03/184752)
- stringクラスのclearは空文字代入と何が違う？
	- 違いはない（空文字代入でも空になる）が、クリアする目的であることを明示できるメリットはある。
- friendって使う？
	- 使わない。
	- 適切に OOAD (Object-Oriented Analysis and Design) ができていればまず使うことは無い/使う必要が無い。[詳細はこちら](https://ja.stackoverflow.com/questions/44299/c-friend%E9%96%A2%E6%95%B0%E3%81%A8friend%E3%82%AF%E3%83%A9%E3%82%B9%E3%81%AE%E9%81%95%E3%81%84%E3%82%92%E7%9F%A5%E3%82%8A%E3%81%9F%E3%81%84%E3%81%A7%E3%81%99)
- イテレータのメリット
	- 配列の長さを求めて足し算して…というコードを自分で書く必要がない
		- 例）イテレータ非使用時
``` c++
int arr[] = { 1, 3, 9, 4 };
for (int idx = 0; idx != (sizeof(arr) / sizeof(arr[0])); ++idx) {
	std::cout << arr[idx] << std::endl;
}
```
		- 例）イテレータ使用時
``` c++
int arr[] = { 1, 3, 9, 4 };
for(int* it = std::begin(arr); it != std::end(arr); ++it){
    std::cout << *it << std::endl;
}
```
- nullptrとNULLの違い
	- NULLは0なので、ポインタ以外にも使える。一方、nullptrは、ポインタ変数以外には使えないため、意図しない使われ方をした場合にコンパイルエラーで防ぐことができる。
- bool型のサイズは？
	- 1Byte
- 参照渡しとポインタ渡し
``` c++
void calc( int x, int &y ) { /* 参照渡し */
	y += x;
}
void calc( int x, int *p ) { /* ポインタ渡し */
	*p += x;
}
int main( void ) {
	calc( x, y );	/* 参照渡し */
	calc( x, &y );	/* ポインタ渡し */
}
```
	- 参照渡しは、VBAでいう"ByRef"だと思えばいい！
	- 参照渡しとポインタ渡しは自動で区別されるため、オーバーロードできる！
- クラステンプレートについて
	- クラステンプレートの場合、インスタンス化はクラステンプレートの完全な定義が必要になったとき初めてインスタンス化され、それ以前までインスタンス化が遅延される。(詳細は[こちら](https://qiita.com/_EnumHack/items/bf6a2209174331b056c1))
	- テンプレートというのは実際に使われていないメソッドに関してはインスタンス化されない。(詳細は[こちら](https://pknight.hatenablog.com/entry/20100316/1268750644))
- テンプレートのインスタンス化の種類
	- 暗黙的インスタンス化
		- テンプレート使用時に自動的にインスタンス化されること。このとき、メンバの定義はインスタンス化されず、そのメンバが実際に使用されるときにまで先送りされる。
	- 明示的インスタンス化
		- あらかじめテンプレートをインスタンス化させておくこと
			`template class Stack<int>;`
		- 明示的インスタンス化をしないと、クラスの宣言だけでなく定義もヘッダファイルに書く必要がある。(詳細は[こちら](https://qiita.com/_EnumHack/items/bf6a2209174331b056c1))
- オーバーライドとオーバーロードの覚え方
	- オーバーライド
		- 派生クラスで基底クラスのメソッドを上書き機能。（＝上書き定義）
		- 英単語override：を乗り越える、～より優位に立つ、～に優先する、～を無効にする、～を覆す、上乗せする
		- 覚え方：オーバー(上に)ライド(乗る＝上書きする)
	- オーバーロード
		- 引数の数や型が少しずつ異なる同名の関数を定義できる機能（＝多重定義）
		- overload:負荷
		- 覚え方：似たような関数が複数に増えるため負荷が増える
- [overrideしたいメンバー関数にvirtualを付け忘れるとどうなるか？](https://www.chihayafuru.jp/tech/index.php/archives/2928)
	- コンパイルエラーになる。
	- 派生クラスを指す基底クラスの参照からメンバ関数を呼び出した時の挙動(GCCにて確認)をまとめると以下の通り。
		- (1) virtualあり(\*1)かつoverrideあり(\*2)の場合…派生クラスのメンバ関数が呼ばれる
		- (2) virtualなし(\*1)かつoverrideあり(\*2)の場合…コンパイルエラーとなる（仮想関数でないのにoverrideをつけると怒られる）
		- (3) virtualあり(\*1)かつoverrideなし(\*2)の場合…派生クラスのメンバ関数が呼ばれる
		- (4) virtualなし(\*1)かつoverrideなし(\*2)の場合…基底クラスのメンバ関数が呼ばれる
			- (\*1) 基底クラスのメンバ関数にvirtualがついているかどうか
			- (\*2) 派生クラスのメンバ関数にoverrideがついているかどうか
	- 上記の通り、override指定子がない場合は基底クラスが仮想関数か否かで振る舞いが変わる。override指定子をつけている場合は、仮想関数であることが必須となるので、仮想関数を完全に上書きしたい場合はoverrideをつけておいたほうが安全。
	- 上の(4)のパターンはoverride指定子をつけていないためオーバーライドなの？と思ってしまうが、メンバ関数を上書きしている以上はこれもオーバーライドといってよい。

[トップに戻る](../index.md)
