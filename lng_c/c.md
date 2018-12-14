# �\��
- �yif�zif ( ������ ) { �` } else if ( ������ ) { �` } else { �` }
- �yswitch�z
- �ywhile�z
- �ydo while�z
- �y�֐���`�z
- �y�ϐ���`�z
- �ytypedef�z
- �yfor�z

- �ydefine�z#define �� (��)
- �yinclude�i�W���j�z #include <stdio.h>
- �yinclude�i���[�U��`�j�z #include "dummy.h"
- �yif�z#if ������ �` #elseif ������ �` #else �` #endif
- �yifdef�z#ifdef ������ �` #else �` #endif
- �yifndef�z#ifdef ������ �` #else �` #endif

- �y�\���́z
- �y���p�́z
- �y�񋓑́z

# Tips
- const
	- const char\* c; /\* Val�F�ύX�~ Adr�F�ύX�� \*/ �� const char �̃|�C���^ c ���`
	- char\* const c; /\* Val�F�ύX�� Adr�F�ύX�~ \*/ �� char �̃|�C���^ c (const) ���`
- �\���̐錾�ɂ���
	- �\���̐錾�͕K�������K�v�Ƃ͌���Ȃ��BA��B�͓�������������B
	- �錾���ꂽ�^���ė��p����ꍇ�͕K�v�����A�ė��p������肪�Ȃ��̂ł���Β�`�݂̂ł悢�B
	- ���K�Ő錾���铮���̂ق����悢�ꍇ�����邪�c
		- A
			``` c 
			volatile struct {
				tBypassHeader  Header;
				volatile uint8 OutputTable1[CDC_MAXPTRB01];
				volatile uint8 OutputTable2[CDC_MAXPTRB01];
			}cdcBypassB01;
			```
		- B
			``` c 
			typedef struct {
				tBypassHeader  Header;
				volatile uint8 OutputTable1[CDC_MAXPTRB01];
				volatile uint8 OutputTable2[CDC_MAXPTRB01];
			}tcdcBypassB01;
			tcdcBypassB01 cdcBypassB01;
			```
- �O���[�o���ϐ���`���ɏ������q��t�����邱�Ƃ����Ȃ��ꍇ������̂͂Ȃ����H
	- �}�C�R���̂悤�ȊJ���ł́A�X�^�[�g�A�b�v�����Ɋ��҂��Ȃ��悤�ɂ��邽�߁B
�i�g�ݍ��݊J���ł́A�������q��ێ�����̈悪�m�ۂ���Ă���Ƃ͌���Ȃ��j
- �R���p�C������Ȃ����Ƃ�����B�B
	- �����r���h�ł́A�R���p�C����C�t�@�C����OBJ�t�@�C���Ƃ̃^�C���X�^���v���r���A
OBJ�t�@�C�����V�����ꍇ�R���p�C�����Ȃ��d�g�݂ƂȂ��Ă���B
- typedef �� define �ɂ���
	- �P�ɓ��`������#define�ɔ�ׁAtypedef �́u�^�v�̓��`������Ƃ����ړI�����m�ł���B
		- http://www9.plala.or.jp/sgwr-t/c/sec16.html
	- ����_
		- define �v���v���Z�b�T�ɂ����߂���Atypedef�̓R���p�C���ɂ����߂���܂��B
		- typedef�̏ꍇ�́A�R���p�C�����^����ێ��B�i�P���ȃ\�[�X�R�[�h������̒u���ł͂Ȃ��I�j
		- �i�����Ȃ�΁u�ϐ��^�ɕʖ��ŃA�N�Z�X���Ă���v��ԁj
		- ���ׁ̈A�f�o�b�K�ŕϐ���ǂ�������ۂɂ��Atypedef�̒�`�͗L���ł��B
		- �i #define���g������`�ł́A�S���l�����Ȃ��b�j
	- �ȉ��͓��`
		``` c 
		#define VAL 0	/* VAL �� 0 �ɒu�������� */
		typedef 0 VAL;	/* 0 �� VAL �Ƃ��ĔF�������� */
		```
	- �������Adefine �͈ȉ��̂悤�ɂ͂ł��Ȃ�
		``` c 
		typedef int arrInt[5]							/* int �� arrInt[5] �Ƃ��čĒ�`���� */
		arrInt a;
		a[0] = 1;
		```
- define �̕s�
	``` c 
	#include <stdio.h>
	
	#define char_ptr  char *
	typedef char * char_ptr2;
	
	int main(void)
	{
		char_ptr1 a1, a2, a3;
		char_ptr2 b1, b2, b3;
		
		printf("%d\n", sizeof(a1)); /* �� 4 */
		printf("%d\n", sizeof(a2)); /* �� 1 */
		printf("%d\n", sizeof(a3)); /* �� 1 */
		printf("%d\n", sizeof(b1)); /* �� 4 */
		printf("%d\n", sizeof(b2)); /* �� 4 */
		printf("%d\n", sizeof(b3)); /* �� 4 */
		
		return 0;
	}
	```
- �֐��|�C���^��
	```c
	#include <stdio.h>
	
	#define FUNC_EXE_DOINCREMENT    ((int)0x01 << 0)
	#define FUNC_EXE_DODECREMENT    ((int)0x01 << 1)
	#define FUNC_EXE_DODOUBLE       ((int)0x01 << 2)
	#define FUNC_EXE_DOTRIPLE       ((int)0x01 << 3)
	#define FUNC_NUM_MAX            ((int)        4)
	
	void    behavior(int intFuncFlag, int intInputVal, int *intOutputVal);
	int     doIncrement(int arg01);
	int     doDecrement(int arg01);
	int     doDouble(int arg01);
	int     doTriple(int arg01);
	void    debugPrint(int arg01);
	
	int     (*fp[FUNC_NUM_MAX])(int)    =   {
												doIncrement,
												doDecrement,
												doDouble,
												doTriple
											};
	
	int main(void)
	{
		int     intInputVal     = 10;
		int     intOutputVal    = 0;
		
		behavior(
					( FUNC_EXE_DOINCREMENT | FUNC_EXE_DODECREMENT | FUNC_EXE_DODOUBLE | FUNC_EXE_DOTRIPLE),
					intInputVal,
					&intOutputVal
				);
	
		printf("OutputVal is %d !", intOutputVal);
	
		return (0);
	}
	
	void behavior(
					int intFuncFlag,
					int intInputVal,
					int *intOutputVal
				)
	{
		int     intLoopCnt  =   0;
		int     intBitMsk   =   0x01;
		
		debugPrint(intFuncFlag);
		
		for (intLoopCnt = 0; intLoopCnt < FUNC_NUM_MAX; intLoopCnt++) {
			if ((intFuncFlag & intBitMsk) == 1) {
				 *intOutputVal   += fp[intLoopCnt](intInputVal);
			}
			intFuncFlag = intFuncFlag >> 1;
		 }
		 
		 return;
	}
	int doIncrement(int arg01)  { return (arg01 + 1); }
	int doDecrement(int arg01)  { return (arg01 - 1); }
	int doDouble(int arg01)     { return (arg01 * 2); }
	int doTriple(int arg01)     { return (arg01 * 3); }
	
	void debugPrint(int arg01)
	{
		printf("debug print \"%d\"\n", arg01);
		return;
	}
	```
- �g���ݗp��
	- ���Z�b�g�x�N�^		
		- �d���������⃊�Z�b�g���ꂽ�����ɁA�^����ɋ����I�Ɏ��s�����A�Z���u���[���x���ł̃v���O�������s�J�n�A�h���X�ł��B	
	- �X�^�[�g�A�b�v���[�`��		
		- �f�[�^�Z�N�V������RAM�ɃR�s�[
		- BSS�Z�N�V�����̏������RAM��ɕϐ���W�J
		- �X�^�b�N�Z�N�V�����̏�񂩂�X�^�b�N�̈���m�ۂ��A�X�^�b�N�̐擪�A�h���X��MPU�̃X�^�b�N�|�C���^�ɐݒ肵�܂��B	
	- �Z�N�V����
		- �e�L�X�g�Z�N�V����	
			- ���߁A�֐��Ȃǂ̏������L�q���Ă���A���s���ɕύX����Ȃ��������i�[����BRAM�ɃR�s�[���ꂸ��ROM�Ɏc��
		- �f�[�^�Z�N�V����	
			- �����l�t���ϐ������i�[����B���s���ɕύX����邽�߁ARAM�ɃR�s�[�����
		- BSS�iBlock Started by Symbol�j�Z�N�V����	
			- �����l�����ϐ����̏��i�ϐ��̃T�C�Y�ƃA�h���X�Ȃǁj���i�[����B���̏������RAM��ɕϐ����z�u�����
		- �X�^�b�N�Z�N�V����	
			- �X�^�b�N�Ɋւ��ăT�C�Y�Ȃǂ̏����i�[����B���̏������RAM��ɃX�^�b�N���m�ۂ����
![�������Z�N�V��������](�������Z�N�V��������.jpg)
- �A���C�������g
	- �\���̂̃T�C�Y�ɂ���
		- �\���̂̃T�C�Y�́A�ő�̒��������v�f�̐����{�ɓ��������Ȃ���΂Ȃ�Ȃ��i�ȉ��̗�Q�Ɓj
			- ���p���Fhttp://www.ertl.jp/~takayuki/readings/info/no01.html
![�A���C�������g��](�A���C�������g��.jpg)
- OS �ɂ���
	- �C���o�[�W����
		- ��
	- �f�b�h���b�N
		- ��
	- �v���C�I���e�B�[�V�[�����O
		- ��
