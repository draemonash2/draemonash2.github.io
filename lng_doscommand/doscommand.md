# ToDo

# Tips
- �o�b�`�t�@�C���ɂ�Path���ݒ肳��Ă��Ȃ��悤�ȋ����ƂȂ�
	- Path �ݒ��AOS �ċN�����Ȃ��ƃo�b�`�t�@�C���ł� Path ���ݒ肳��Ȃ�
- �V���{���b�N�����N�ɂ���
	-  �V���{���b�N�����N�^�n�[�h�����N�^�V���[�g�J�b�g�̈Ⴂ
		- http://qiita.com/opengl-8080/items/c2b6a93dfca5b61f9e6a
	- �V���{���b�N�����N�i�t�H���_�j���s��
		- mklink /d "C:\Users\draem\_000\AppData\Roaming\Apple Computer\MobileSync\Backup" "X:\810\_BackUp\_iTunes\MobileSync\Backup"
		```
		�y�����N���z
		  C:
		  �� Users
			�� draem\_000
			  �� AppData
				�� Roaming
				  �� Apple Computer
					�� MobileSync
					  �� Backup
		�y�����N��z
		  X:
		  �� 810\_BackUp\_iTunes
			�� MobileSync
			  �� Backup
				�� e197dbc615bfdf9375672cf9b26f6928bb655cb3
		�y�\����z
		  C:
		  �� Users
			�� draem\_000
			  �� AppData
				�� Roaming
				  �� Apple Computer
					�� MobileSync
					  �� Backup�i��X:\810\_BackUp\_iTunes\MobileSync\Backup�j
						�� e197dbc615bfdf9375672cf9b26f6928bb655cb3 
		```
- �t�@�C���p�X�W�J�ɂ���
	- I:�����i0:���s���̃o�b�`�t�@�C���A1�`:�o�b�`�t�@�C���̈����j
 [�p�X]   [����]                  [�o�͌���]
 %I       �����񂻂̂܂�          "C:\Users\draem\_000\Desktop\test\test 1-1.bat"
 %~I      ���ׂĂ̈��p�� " �폜   C:\Users\draem\_000\Desktop\test\test 1-1.bat
 %~fI     ���S�C���p�X��          C:\Users\draem\_000\Desktop\test\test 1-1.bat
 %~dI     �h���C�u����            C:
 %~pI     �p�X                    \Users\draem\_000\Desktop\test\
 %~dpI    �f�B���N�g���p�X        C:\Users\draem\_000\Desktop\test\
 %~nI     �t�@�C����              test 1-1
 %~xI     �t�@�C���g���q          .bat
 %~sI     �Z���p�X                C:\Users\DRAEM\_~1\Desktop\test\TEST1-~1.BAT
 %~aI     �t�@�C������            --a--------
 %~tI     �t�@�C�����t/����       2016/10/27 16:11
 %~zI     �t�@�C���T�C�Y          1397
- ���C���h�J�[�h���g�p���āA�e�L�X�g�t�@�C�����ꊇ�ύX����
	- rename \*.txt \*.xls
- SET ���̊ԂɃX�y�[�X�͓���Ȃ��I
	``` bat
	:: <<OK ��>>
	set ARG\_NUM=9
	echo %ARG\_NUM%
	:: �� 9

	:: <<NG ��>>
	set ARG\_NUM = 9
	echo %ARG\_NUM%
	:: �� ECHO �� OFF �ł�
	```
- if ���Ŕ��肷��ϐ��ɉ��������Ă��Ȃ��\��������ꍇ�́A���̕ϐ��� if ���Ŏg�p����ۂ� "" �� {} �ň͂����ƁI
	``` bat 
	:: <<NG��>>
	::  �uif %2 == /a�v�́A������������Ȃ��ꍇ�u( �̎g����������Ă��܂��B�v�Ƃ����G���[�ɂȂ�B
	::  ���̗�̒��̂ł́A�����P�� 1 �������Ă��āuif %2 == /a�v�̃p�X���ʂ�Ȃ��Ă��A�ŊO����if�����ꕶ�Ƃ��ĂƂ炦���邽�ߏ�L�Ɠ��l�G���[�ɂȂ�B
	if %1 == 2 (
		if %2 == /a (
			echo a
		) else (
			echo b
		)
	) else (
		echo c
	)
	
	:: <<OK��>>
	::  �uif "%2" == "/a"�v�́A������������Ȃ��ꍇ�ł��G���[�ɂȂ�Ȃ����߁A����ɓ��삷��B
	if "%1" == "2" (
		if "%2" == "/a" (
			echo a
		) else (
			echo b
		)
	) else (
		echo c
	)
	```
- if ���̒��ɃR�����g�͓���Ȃ��I
- FOR����IF���ŕϐ��̒��g��������
	- �ڍׂ͈ȉ�
 http://d.hatena.ne.jp/jak-san/20110709/1310168663
- setlocal / endlocal�R�}���h�͊��ϐ��̃��[�J�����̂��߂ɂ���܂��B
	- ���[�J�����Ƃ�setlocal����endlocal�͈͓̔��Œ�`�����ϐ������̒������L���ł��̊O���̓����̕ϐ��ɉe�����y�ڂ��Ȃ��悤�ɂ��邱�Ƃł��B
- ��̃R�}���h�𕡐��s�ɕ����ċL�q������@
	- �s���Ɂu^�v���L�q����B�Q�s�ڈȍ~�͍s���ɋ󔒂��L�ڂ��邱�ƁB
		```
		"C:\prg\_exe\Vim\gvim.exe" ^
		  "c:\work1\test.c" ^
		  "c:\work2\test.h" ^
		  ""
		```
- �ustart�v�R�}���h�Ɓu�X�y�[�X�v�̑����������I
	- http://d.hatena.ne.jp/mizuki\_astral/20100715/1279203356
- pushd �R�}���h
	- cd �R�}���h�̓h���C�u���ׂ����ړ����ł��Ȃ��B�i/d �I�v�V�������K�v�j
	- pushd �R�}���h�̓h���C�u���ׂ����ړ����ł���I

# �\��

- �y�ϐ���`�zset LOGDIR=C:\Users\Dropbox
- �y�񋓌^��`�z-
- �y�u���b�N�E�o�z-
- �y�w���v�zhelp dir

- �yif�zif %TAG\_TYPE% == a ( �`�����` ) else if %TAG\_TYPE% == c ( �`�����` ) else ( �`�����` )
- �yif�i�ے�j�zif not %TAG\_TYPE% == a
- �yfor�z��
- �y�R�����g�z::�R�����g
- �y�o�́zecho Hello world!
- �y�o�́i���s�̂݁j�zecho.
- �y�o�͗}���z\>NUL 2>&1

- �y������ �؎�P�z%VAR% �˕ϐ�V�̒l�S��
- �y������ �؎�Q�z%VAR:~m% ��m�����ڂ���A�Ō�܂�
- �y������ �؎�R�z%VAR:~m,n% ��m�����ڂ���An������
- �y������ �؎�S�z%VAR:~m,-n% ��m�����ڂ���A�Ō��n������������������
- �y������ �؎�T�z%VAR:~-m% �ˌ�납��m�����ڂ���A�Ō�܂�
- �y������ �؎�U�z%VAR:~-m,n% �ˌ�납��m�����ڂ���An������
- �y������ �؎�V�z%VAR:~-m,-n% �ˌ�납��m�����ڂ���A�Ō��n������������������
- �y������ �؎�W�z%VAR:c1=c2% �˕���c1�𕶎�c2�ɒu������B���ꂼ�ꕡ���̕������w�肷�邱�Ƃ��\

- �y�t�@�C�� �폜�zdel /a /q "c:\test\a.txt"
	- <<�I�v�V����>>
		- /a�F�ǂݎ���p�A�V�X�e���t�@�C���A�B���t�@�C���A�A�[�J�C�u���܂߂č폜
		- /q�F�폜�O�Ɋm�F���b�Z�[�W��\�����Ȃ�
		- /s�F�w�肳�ꂽ�t�@�C�������ׂẴT�u�f�B���N�g������폜����
	- <<���p��>>
		- "C:\test\b" �t�H���_�z���i�T�u�f�B���N�g���܂ށj�ɂ��� .dat �t�@�C���S�폜
			- del /s /a /q "C:\test\b\\*.dat"
- �y�t�@�C�� �ړ��zmove "c:\test\a.txt" "c:\test\dst"
- �y�t�@�C�� �R�s�[�zcopy "c:\test\a.txt" "c:\test\dst"
- �y�t�H���_ ���̕ύX�zrename "c:\test\a.txt" "b.txt"
	- <<���L����>>
		- �ύX��̃t�@�C�� &bold(){��} ���w�肵�܂��B�p�X���w�肷�邱�Ƃ͂ł��܂���B

- �y�t�H���_ �쐬�zmkdir "c:\test\a"
- �y�t�H���_ �폜�zrmdir /s /q "c:\test"
	- <<�I�v�V����>>
		- /s�F�t�@�C����T�u�f�B���N�g�����܂߂č폜����
		- /q�F/s�ō폜����ۂɊm�F���b�Z�[�W��\�����Ȃ�
- �y�t�H���_ �ړ��zmove "c:\test\src" "c:\test\dst"
	- <<���L����>>
		- "c:\test\dst\src" ���쐬�����B
- �y�t�H���_ �R�s�[�zecho d | xcopy /e /h /r /y "c:\test\src" "c:\test\dst\src"
	- <<���L����>>
		- �t�H���_���t�@�C�����𕷂���邽�߁A�uecho d�v���K�v�B
		- �uxcopy /e /h /r /y "c:\test\src" "c:\test\dst"�v�ł́A"c:\test\dst\src" ��艺�̃t�@�C��/�t�H���_�̓R�s�[����邪�A"src" �t�H���_���̂̓R�s�[����Ȃ��B
	- <<�I�v�V����>>
		- /e�F�t�@�C�������݂��Ȃ��Ă��f�B���N�g�����ƃR�s�[����
		- /h�F�B���t�@�C����V�X�e���t�@�C�����S�ăR�s�[����
		- /r�F�ǂݎ���p�����̃t�@�C�����㏑���R�s�[�ł���悤�ɂ���
		- /y�F�����̃t�@�C�������݂���ꍇ�A�㏑���̊m�F���s��Ȃ�
		- /-y�F�����̃t�@�C�������݂���ꍇ�A�㏑���̊m�F���s��
- �y�t�H���_ ���̕ύX�zrename "c:\test\_old" "test\_new"
	- <<���L����>>
		- �ύX��̃t�H���_ &bold(){��} ���w�肵�܂��B�p�X���w�肷�邱�Ƃ͂ł��܂���B
- �y�t�H���_�����zrobocopy "c:\test\src" "c:\test\dst" /MIR /XD "System Volume Information"
	- <<���L����>>
		- "c:\test\src\a.txt" �� "c:\test\dst\a.txt" �Ƃ��ăR�s�[�����C���[�W
	- <<�I�v�V����>>
		- /MIR�F�f�B���N�g�� �c���[���~���[������B
		- /XD dir [�f�B���N�g��]... �F�w�肳�ꂽ���O/�p�X�Ɉ�v����f�B���N�g�������O����B
		- /XF file [�t�@�C��]... �F�w�肳�ꂽ���O/�p�X/���C���h�J�[�h�Ɉ�v����t�@�C�������O����B

- �y�t�@�C�����t�H���_ �c���[�擾�z�i�B���t�@�C���A�V�X�e���t�@�C���͕\���ł��Ȃ��j
	- �y�t�@�C�����t�H���_�ztree /f
	- �y�t�H���_�̂݁ztree
- �y�t�@�C�����t�H���_ �ꗗ�擾�z�i�B���t�@�C���A�V�X�e���t�@�C���܂ށj
	- �y�t�@�C�����t�H���_�zdir /b /s /a
	- �y�t�H���_�̂݁zdir /b /s /a:d
	- �y�t�@�C���̂݁zdir /b /s /a:a-d
		- �y.c�A.h�t�@�C���̂�(��)�zdir \*.c \*.h /b /s /a:a-d
			- (��)�u\*.cc�v�̂悤�ȁu\*.c�v�𕶎���Ƃ��Ċ܂܂��g���q�͏Ȃ����B�֗��I

- �y�V�X�e�������ݒ�zattrib +S C:\test.txt
- �y�V�X�e�����������zattrib -S C:\test.txt
- �y�B�������ݒ�zattrib +H C:\test.txt
- �y�B�����������zattrib -H C:\test.txt

- �y�Q����ɃV���b�g�_�E���zshutdown /s /t 120
- �y�Q����ɍċN���zshutdown /r /t 120
- �y�V���b�g�_�E�����L�����Z���zshutdown /a

- �y�V���{���b�N�����N�쐬�i�t�H���_�j�zmklink /d "c:\test" "d:\program files\test"
- �y�V���{���b�N�����N�쐬�i�t�@�C���j�zmklink "c:\test.txt" "d:\program files\test.txt"

- �y�x���W�J�ϐ��ݒ�zsetlocal ENABLEDELAYEDEXPANSION �` endlocal

- �y�v���O�����I���zexit /B 0

- �y���ϐ� �ݒ�zsetx MYPATH\_CODES "C:\codes"
- �y���ϐ� �����zreg delete HKCU\Environment /v MYPATH\_CODES
- �y���ϐ� ���݊m�F�zif {%MYPATH\_CODES%} == {0} ( �`���ϐ��������݁` )

- �yWindows 60�b��ɃV���b�g�_�E���zshutdown -s -t 60
- �yWindows 60�b��ɍċN���zshutdown -r -t 60

- for ���ɂ���
	- [�Q�l] http://qiita.com/sawa\_tsuka/items/67be34bab1fdf3fb87f9
	- FOR (�I�v�V����) %%�A���t�@�x�b�g�P���� IN (���[�v�����̑Ώ�) DO �R�}���h
		- <<�I�v�V����>>
			- (�I�v�V��������)�F�t�H���_����ΏۂɂƂ�
			- /D�F�t�H���_����ΏۂɂƂ�
			- /R�F�t�H���_���y�т��̃T�u�t�H���_���i���̃t�H���_�̒��̃t�@�C������t�H���_���j��ΏۂɂƂ�
			- /L�F�l���w�肵�đ������
			- /F�F�e�L�X�g�t�@�C�����̕��͂ɑ΂��ăg�[�N�������o���đ������
	- �y�t�H���_���ΏہzFOR %%�A���t�@�x�b�g�P���� IN (���[�v�����̑Ώ�) DO �R�}���h �i��F FOR %%I IN (\*.bat) DO TYPE %%I�j
	- �y�t�H���_���̃f�B���N�g���̂݁zFOR /D (�t�@�C���p�X) %%�A���t�@�x�b�g�P���� IN (���[�v�����̑Ώ�) DO �R�}���h �i��F FOR /D C:\ %%I IN (\*.txt) DO TYPE %%I�j
	- �y�t�H���_�z���̒��g�S���zFOR /R (�t�@�C���p�X) %%�A���t�@�x�b�g�P���� IN (���[�v�����̑Ώ�) DO �R�}���h �i��F FOR /R C:\ %%I IN (\*.txt) DO TYPE %%I�j
	- �y�ϐ��ɒl�������ăR�}���h�����s�zFOR /L %%�A���t�@�x�b�g�P���� IN (�J�n�l�A�����A�I���l) DO �R�}���h �i��F FOR /L %%I IN (1,2,10) DO ECHO %%I�j
	- �y���̑��zFOR /F "�g�[�N���I�v�V����" %%�A���t�@�x�b�g�P���� IN (���[�v�����̑Ώ�) DO �R�}���h
		- <<�g�[�N���I�v�V����>>
			- tokens= �F���Ԗڂ̃g�[�N�����w�肷�邩�H
			- delims= �F�g�[�N���̋�؂蕶�����w��
			- eol= �F���̕�������n�܂�s�𖳎�
			- skip= �F�擪����w�肳�ꂽ�s���A�X�L�b�v����B
			- usebackq �F�R�}���h�̏o�͂�Ώۂɂ���

# �T���v���R�[�h
- �y�t�H���_/�t�@�C���폜�z
	- �o�b�`�t�@�C���jDelFileOrFolder.bat
	- �g�����jcall DelFileOrFolder.bat c:\test\path�i�p�X�̓t�H���_���t�@�C���o���w��\�j
		```
		@echo off
		
		setlocal
		
		set JDG\_FILE=%~a1
		set FILE=%1
		
		::�t�@�C�����݊m�F
		if not exist %FILE% goto end
		
		::�t�@�C�������݂����ꍇ�A�폜
		if %JDG\_FILE:~0,1% == d (
			rmdir /S /Q %FILE%
			echo Directry %FILE% is Deleted!
		) else if %JDG\_FILE:~0,1%==- (
			del /Q /F %FILE%
			echo File %FILE% is Deleted!
		) else (
			echo %FILE% is not File/Folder Path!
		)
		
		:end
		endlocal
		```
- �����̐��`�F�b�N
	```bat
					 set ARG\_NUM=9
	if "%~9" == "" ( set ARG\_NUM=8 ) else ( goto exec )
	if "%~8" == "" ( set ARG\_NUM=7 ) else ( goto exec )
	if "%~7" == "" ( set ARG\_NUM=6 ) else ( goto exec )
	if "%~6" == "" ( set ARG\_NUM=5 ) else ( goto exec )
	if "%~5" == "" ( set ARG\_NUM=4 ) else ( goto exec )
	if "%~4" == "" ( set ARG\_NUM=3 ) else ( goto exec )
	if "%~3" == "" ( set ARG\_NUM=2 ) else ( goto exec )
	if "%~2" == "" ( set ARG\_NUM=1 ) else ( goto exec )
	if "%~1" == "" ( set ARG\_NUM=0 ) else ( goto exec )
	:exec
	```
- �w��t�H���_�z���� .svn �t�H���_�����ׂč폜
	```bat
	cd "C:\Users\draem\_000\Desktop\codes\_sample"
	for /R %i in (.svn) do rmdir /Q /S "%i"
	```
- bat �t�@�C���ŃR���\�[�����J�����ɃR�}���h���s����
	```bat
	@echo off
	
	if not "%~0"=="%~dp0.\%~nx0" (
		 start /min cmd /c,"%~dp0.\%~nx0" %\*
		 exit
	)
	
	start "C:\prg\_exe\Vim\gvim.exe" "C:\test.txt"
	```
