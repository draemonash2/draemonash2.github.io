[トップに戻る](../index.md)

# 構文

- 参考URL：[Fortran90](https://www.rs.kagu.tus.ac.jp/yama/f90/f90-lang.html)
- 参考URL：[Fortran90を用いたプログラミングの記述方法＠JAMSTEC](https://www.jamstec.go.jp/es/jp/simschool/f90learning/index.html)

- 【変数定義】REAL :: A,B,C,X
	- データ型
		- 【INTEGER】整数型
		- 【REAL】実数型
		- 【DOUBLE PRECISION】倍精度実数型（有効桁数が2倍）
		- 【COMPLEX】複素数型
		- 【CHARACTER】文字型
- 【変数定義(配列)】REAL, DIMENSION(10) : : a !要素番号は1オリジン
- 【定数定義】REAL, PARAMETER : : one = 1.0
- 【変数参照(配列)】a(1)
- 【コメント】!
- 【開始】PROGRAM プログラム名
- 【終了】END PROGRAM プログラム名
- 【算術演算子(べき乗)】A\*\*B
- 【暗黙の型宣言無効化】IMPLICIT NONE
- 【入力】READ (\*,\*) A,B,C !入力文
- 【出力】WRITE(\*,\*) 'X = ' , X
- 【プログラム中止】STOP #C言語でいうRETURNみたいなもの？★
- 【IF】IF (条件式A) THEN ～ (条件式A＝真) ～ ELSE IF (条件式B) THEN ～ (条件式B＝真) ～ ELSE ～ (条件式B＝偽) ～ END IF
- 【DO】DO I=5,10 ～処理～ END DO
- 【論理演算子(AND)】90.0 <= SCORE(I) .AND. SCORE(I) <= 100.0
- 【論理演算子(OR)】90.0 <= SCORE(I) .OR. SCORE(I) <= 100.0
- 【論理演算子(NOT)】.NOT. (90.0 <= SCORE(I))
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
