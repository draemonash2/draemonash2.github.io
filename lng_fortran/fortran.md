[トップに戻る](../index.md)

# 構文

- [構文はこちら参照](https://www.rs.kagu.tus.ac.jp/yama/f90/f90-lang.html)

- 【変数定義】real :: a,b,c,x
	- データ型
		- 【integer】整数型
		- 【real】実数型
		- 【double precision】倍精度実数型（有効桁数が2倍）
		- 【complex】複素数型
		- 【character】文字型
- 【変数定義(配列)】real, dimension(10) :: a !要素番号は1オリジン
- 【変数参照(配列)】a(1)
- 【コメント】!
- 【開始】program プログラム名
- 【終了】end program プログラム名
- 【算術演算子(べき乗)】a\*\*b
- 【暗黙の型宣言無効化】implicit none
- 【入力】read (\*,\*) a,b,c !入力文
- 【出力】write(\*,\*) 'x = ' , x
- 【プログラム中止】stop #C言語でいうreturnみたいなもの？★
- 【if】if (条件式A) then ～ (条件式A＝真) ～ else if (条件式B) then ～ (条件式B＝真) ～ else ～ (条件式B＝偽) ～ end if
- 【do】do i=5,10 ～処理～ end do
- 【論理演算子(AND)】90.0 <= score(i) .and. score(i) <= 100.0
- 【論理演算子(OR)】90.0 <= score(i) .or. score(i) <= 100.0
- 【論理演算子(NOT)】.not. (90.0 <= score(i))
- 【比較演算子(＜)】<
- 【比較演算子(≦)】<=
- 【比較演算子(＝)】=
- 【比較演算子(≧)】>=
- 【比較演算子(＞)】>
- 【比較演算子(≠)】/=
- 【】
- 【】
- 【】
- 【】
- 【】
- 【】
- 【】
- 【】
- 【】
- 【】
- 【】
- 【】

# Tips
- コンパイル方法
	- gfortran -o 出力ファイル名 ソースファイル名





[トップに戻る](../index.md)
