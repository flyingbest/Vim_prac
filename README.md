손에 잡히는 Vim	- getting started with vim
======
------

### Vim의 배경과 설치

> 라인 에디터부터 Vi 와 Vim 까지

Vim은 Vi를 발전시킨 'Vi improved'에서 앞글자를 빼내 만든 이름.

Vim의 원조격인 Vi는 빌 조이가 만들어 오랫동안 유닉스 세상에서 사랑받은 에디터이다. 빌 조이는 유닉스의 창시자였던 켄 톰슨의 동료이자 제자이고, BSD 유닉스의 초기 개발자이기도 하다. 또한 솔라리스 유닉스와 자바로 유명한 썬마이크로시스템즈의 공동 창업자 이기도 하다.

> Vi, Vim의 장점

Vi와 Vim은 기본적으로 텍스트 환경의 사용자 인터페이스(CUI)를 사용하고 있다. 물론 Vi, Vim 외에도 유닉스 계열에서 작동하는 대부분의 프로그램이 CUI 방식을 사용한다.

CUI를 사용하는 이유는 성능 때문. 서버에는 여러 유저가 네트워크로 접속해서 프로그램을 실행하므로 용량이 크고 느린 프로그램은 심각한 문제를 초래. 그렇기 때문에 서버 환경에서는 Vi나 Vim 같이 가볍고 빠른 프로그램이 선호된다.

> Vim 과 이맥스(Emacs)

유닉스나 리눅스에서는 Vim 외에도 이맥스(Emacs)라는 유명한 에디터가 있다. 이맥스는 프로그래밍에 최적화된 에디터로, 디버거나 다른 외부 프로그램과의 연동, 플러그인의 확장 등이 매우 강력하다. 이 에디터는 해커들을 위한 강력한 프로그래밍 환경이 필요하다고 생각한 자유소프트웨어재단(Free Software Foundation)의 설립자 리처드 스톨만이 만들었다. 프로그래밍 환경을 개선하려는 목적은 Vi와 같지만, 이맥스는 더 나중에 만들어진 에디터이고 리차드 스톨만 본인이 뛰어난 해커다보니 프로그래머의 가려운 부분을 굵어줄 형태가 되었다.

이맥스의 기능은 다른 IDE 개발 인터페이스에도 영향을 끼쳤는데, 이클립스(Eclipse)와 같은 IDE 개발툴은 이맥스와 단축키 구성이 거의 흡사할 정도이다. 이 외에 다른 많은 프로그래밍 유틸리티들도 이맥스와 자연스럽게 연동되거나 인터페이스가 비슷하다. 그러나 이맥스는 프로그래밍에 최적화되어있다 보니 범용 에디터로는 적합하지 않다는 의견도 많다. 이맥스는 그 기능이 Vim보다 훨신 방대하므로 Vim 배우고 나서 이맥스를 배우도록!

> Vim 설치 (데이안 계열, Wimdows)

Vim 설치 완료!

------

### Vim 입문

_모르는 것만 입력!_

> 모드가 필요한 이유

입력 ㅁ드와 일반 모드를 따로 둔 이유는, Vim을 개발할 당시에는 기능을 호출하는 데 메뉴 인텊이스를 사용할 수 없었기 때문이다. 현대적인 컴퓨팅 환경은 그래픽 표현을 지원하기 때문에 메뉴나 버튼, 창에 기능을 넣을 수 있지만, Vim의 모태인 Vi가 개발되던 시절에는 이런 고급스런 그래픽 환경이 존재하지 않았다. 모든 화면은 텍스트로만 출력이 되었다. 이런 상황에서 어떻게 메뉴와 같은 기능을 구현??

단축키! 하지만 이 경우 프로그램에서 사용 가능한 단축키의 숫자가 크게 제한된다. 왜냐하면 일반적인 유닉스 계열 터미널에서는 미리 예약된 단축키가 있기 때문.

따라서 <CTRL> 이나 <ALT> 같은 특수키를 사용하지 않고도 단축키를 지정하기 위해, 단축키 호출 모드를 따로 만든 것이 바로 일반 모드이다. 이렇게 하면 예약된 단축키 조합을 피해갈 수 있기 때문에 키보드의 수많은 키를 전부 사용할 수 있고, 대소문자도 구별할 수 있다.

> Vim의 모드 전환

Vim의 모드를 상세하게 나누면 꽤 많지만 기본적으로는 네 개 정도로 나눌 수 있다. 이 중에서도 Vi와 호환되는 기본 모드는 일반모드, 입력모드, 명령행모드 이다.

명령어|설명
------|----
입력모드|
a, A|a(append)는 현재 커서 위치에서 한 칸 뒤로 이동한 후 입력 모드로 전환. A는 현재 행의 끝으로 이동 후 입력 모드로 전환
i, I|i(insert)는 현재 커서 위치에서 입력 모드로 전환. I는 현재 행의 맨 앞으로 이동 후 입력 모드로 전환
o, O|o(open line)는 현재 행 아래에 새로운 행을 하나 만든 후 입력 모드로 전환. O는 현재 행 위에 새로운 행을 하나 만든 후 입력 모드로 전환.
R|수정(replace) 모드로 작동하므로 모든 글자는 덧쓰여짐.
저장과 종료|
:w|write, 현재 파일을 저장.
:q|quit, vi를 종료.
:wq|저장하고 종료.
:w filename|filename에 해당하는 파일에 저장.(사본을 만드는 명령)
:q!|변경된 내용을 버리고 vi를 종료.
:w! filename|filename에 해당하는 파일을 덮어쓴다.
:wq! filename|filename에 해당하는 파일을 덮어쓰고 종료.
커서이동|
[#]h|좌로 #칸 이동, #의 생략 시는 1칸
[#]j|아래로 #칸 이동, 	''
[#]k|위로 #칸 이동, 	''
[#]l|우로 #칸 이동, 	''
^|행의 맨 앞으로 이동(공백은 제외)
$|행의 맨 끝으로 이동
화면 스크롤|
\<Ctrl\>+B|위로 한 화면 스크롤
\<Ctrl\>+F|아래로 한 화면 스크롤
\<Ctrl\>+U|위로 1/2 화면 스크롤
\<Ctrl\>+D|아래로 1/2 화면 스크롤
특정위치로 이동|
[#]gg|#행으로 이동. #이 생략되면 1을 의미.
[#]G|#행으로 이동. #이 생략되면 마지막 행을 의미.
:#|#행으로 이동.
현재 위치 확인|
\<Ctrl\>+G|현재 문서 위치 정보를 하단 상태 바에 표시.(:file 도 같은 기능)


> 삭제, 복사, 붙이기, 취소

Vim 의 삭제 키에는 중요한 차이점이 하나 있다. 삭제란 상식적으로 커서 뒤의 문자를 지우는 것. 물론 Vim도 마찬가지로 커서 뒤의 문자를 지우지만, 행 끝에 도달하면 앞의 문자를 지우는 백스페이스로도 작동한다는 점이 다르다. 이를 유식하게 표현하면, Vim에서는 삭제 키로 개행 문자를 지우지 못한다고 말할 수 있다.

사실 Vim에는 지우는 기능이 없다. Vim에서는 삭제 기능이 무조건 잘라내기로 작동한다. 그리고 삭제된 내용은 임시 저장소 역할을 하는 레지스터(register)에 저장된다. 

명령어|설명
---|---
삭제|
x|커서에 위치한 문자 삭제(\<Delete\> 키와 같음)
dd|현재 행을 삭제(반복수를 지정하면 반복수 만큼 명령 반복)
:d|명령행 모드의 명령이라 반복수를 지정할 수 없음.
D|현재 컬럼 위치에서 현재 행의 끝부분까지 삭제(d$와 동일)
J|아래 행을 현재 행의 끝에 붙임(아래 행의 앞부분 공백은 제거됨-공백하나로 치환), 커서의 위치가 행의 끝이 아니라도 작동.
붙이기|
p|현재 행에 붙여 넣는다(put). 개행 문자가 포함된 경우에는 현재 행의 아래에 붙여 넣는다.
:pu|명령행 모드의 명령이라 반복수를 지정할 수 없음.
P|현재 행의 위쪽에 붙인다.
복사|
yy|현재 행을 레지스터에 복사(yank)한다.(일반모드 명령이라 반복수 지정 가능)
:y|		''
Y|		''
undo와 redo|
u|undo 기능이다. 바로 이전에 행한 명령 하나를 취소.
\<Ctrl\>+R|redo 기능이다. 바로 이전에 취소했던 명령을 다시 실행.


- tip! 이전 명령어 반복하기

마침표(.)는 바로 이전에 행한 동작을 다시 반복해 준다. 여기서 바로 이전에 행한 동작이란 입력 모드에서는 \<ESC\> 를 누르기 전까지의 행동이며 일반 모드라면 바로 전에 내린 명령어 키이다. 예를 들어 일반 모드에서 IHello라는 명령을 입력하면 I로 인해 입력보드로 변경되면서 행의 맨 앞으로 이동할 것이다. 곧이어 Hello가 입력된다. 이제 \<ESC\>를 눌러 일반 모드로 돌아가 마침표(.)를 눌러보면 어떻게 작동하는지 쉽게 이해할 수 있다.

명령어|설명
---|---
범위 지정|
:20d|20번 행을 삭제
:10,25d|10~25번 행을 삭제
:10,$d|10~마지막 행까지 삭제
:%y|문서 전체를 복사. %는 1,$와 동일하다.
:.,+20y|현재 행부터 아래로 스무 행을 복사.
:-10,+5d|현재 행부터 위로 10행, 아래로 5행, 총 열여섯 행을 삭제.
:40pu|40번 행에 레지스터의 내용을 붙여넣는다.
|범위 지정에 쓰이는 특수 기호(메타문자)
.|현재 행을 의미
$|마지막 행을 의미
+#|현재 위치에서 #만큼 아래 행을 의미
-#|현재 위치에서 #만큼 위 행을 의미
%|문서(파일) 전체를 의미
비주얼 모드|
v|일반 비주얼 모드로 현재 커서 위치에서 블록을 지정
V|비주얼 라인 모드로, 현재 커서가 위치한 행에서 행 단위로 블록을 지정
\<Ctrl\>+V|비주얼 블록 모드로, 열(column) 단위로 블록을 지정.

간혹 몇명 버전의 윈도 Vim 에서는 방향 키를 누를 때 비주얼 보드가 해제되는 버그가 존재하는데, 이때는 \<Shift\> 키와 함께 눌러주면 잘 작동한다. 물론 가만히 있을 때는 \<Shift\> 키를 누르지 않아도 됨.

---

### 옵션, 도우말, 에러 처리

> Vim 의 옵션

명령어|설명
---|---
:set|현재 옵션 설정을 보여준다.
:set all|모든 옵션 설정을 보여준다.(off 상태의 옵션까지)
:set [no]name|name에 해당하는 옵션을 켜거나 끈다. 앞에 no를 붙이면 off상태가 된다.
:set name!|name 옵션의 on, off 상태를 전환(toggle)한다.
:set name=value|name에 해당하는 옵션에 value 값을 할당. name만 지정하면 해당 옵션의 value 값을 보여준다.

~/.vimrc 설정파일 저장할 수 있다. 옵션과 색상 테마 등..

> 도움말 사용

모든 기능을 다룰 수 없다. 그러므로 나머지 기능은 도움말이라는 좋은 기능을 활용해 알 수 있다.

- 도움말 보기

도움말은 :help topic 명령으로 볼 수 있으며 topic 부분에 궁금한 기능의 이름을 넣어주면 된다. 예를 들어 :help w 명령과 :help :w 명령은 전혀 다른 내용을 보여준다. 

도움말에 사용되는 접두어

모드|접두어|예
---|---|---
일반모드|없음|:help x
입력모드|i\_|:help i\_CTRL-N
명령행모드|:|:help :w
비주얼모드|v\_|:help v\_u
vim 실행인수|-|:help -r
옵션|'|:help 'tabstop'
명령행 모드 특수키|c\_|:help c\_CTRL-B


Vim 의 도움말은 하이퍼텍스트처럼 서로 연결되어 있으므로, 궁금한 태그가 있으면 즉시 이동하여 내용을 확인하고 되돌아오면 된다. 

타이틀(태그) 이동 관련 명령어

명령어|설명
---|---
CTRL-]|커서가 위치한 타이틀(태그)로 이동.
CTRL-T|이전 타이틀(태그)로 이동.
:tags|현재 이동한 타이틀(태그)들의 리스트를 보여준다.

-----

### 문자열 관련 기능

> 문자열 정렬

기본적으로 왼쪽 정렬을 사용한다. 그러나 문서를 작성하다보면 가운데 정렬이나 오른쪽 정렬을 써야할 필요가 있다. 그래서 깔끔하게 명령어로 열의 크기를 계산해서 자동으로 정렬해주는 기능이 필요. 다만 Vim은 문자열과 너비를 계산해서 스페이스를 넣어주는 형태로 정렬하므로, 행의 내용이 수정되면 다시 정렬해야 한다. 

가운데 정렬 :center, 오른쪽 정렬 :right, 문자열 너비 설정 :set textwidth(tw) 명령으로 center나 right 명령어에 인수를 지정해주면 된다.

> 문자, 문자열 검색

- 문자 검색하기

보통 문자 검색하기는 구분 문자(separator)를 찾아낸다든지 할 때 유용하게 사용된다. clientlist.txt 파일은 쉼표를 구분자로 사용하고 있는 CSV(Comma Separated Values) 형식이므로, 편집하거나 각 필드를 볼 때는 쉼표 단위로 이동하는 것이 편리하다.

f는 다음에 나오는 문자를 탐색하라는 명령이다. 세미콜론은(;)은 '다음 검색' 명령이며, 쉼표(,)는 '이전 검색' 명령이다. 주의할 점은 f의 검색 기능은 현재 행에서만 작동하므로 행의 끝까지 이동하면 다음 행으로는 이동하지 않는다는 점이다.

명령어(c는 사용자가 입력한 문자)| 설명
---|---
fc|문자 c를 전방 검색한다.
Fc|문자 c를 후방 검색한다.
tc|문자 c를 전방 검색하여, 검색어의 한 칸 앞으로 이동.
Tc|문자 c를 후방 검색하여, 검색어의 한 칸 뒤로 이동.
;|가장 최근에 검색한 명령을 재검색한다.
,|가장 최근에 검색한 명령을 반대 방향으로 재검색한다.

- 문자열 검색

문자열 검색이란 하나 이상의 문자나 기호, 공백으로 구성된 문장 혹은 패턴을 찾는 기능이다. 일반 모드에서 /re라고 입력하면 문자열 re를 검색한다. 여기서 슬래시 문자(/)는 검색하는 기능을 호출하며, 명령행 모드를 호출하는 콜론(;)처럼 커서가 하단으로 이동한다.

명령어| 설명
---|---
검색 후 이동|
n|다음 검색 결과로 이동.
N|반대 방향의 검색 결과로 이동.

정규 표현식(REGEX)을 사용하면 더욱 폭넓은 검색이 가능하다. /[a-g]re 라고 검색하면 a에서 g까지 영문자 하나로 시작하고 re로 끝나는 문자열을 검색한다.

- 커서 위치의 단어 검색

커서가 위치한 특정 단어를 검색하는 경우에는 단어를 입력하는 대신 별표(\*)를 누르면 된다. 하지만 별표로 검색하면 단어 단위로만 검색하게 된다. 따라서 앞뒤로 공백이 있거나 문장부호로 분리된 문자열만 검색된다. 화면 하단에 나타나는 검색어도 정규 표현식인 \\<단어\\> 로 바뀐다.

> 문자열 교체

교체(substitution) 명령은 명령행 모드에서 사용한다. 

John Patrick.txt 파일의 일반 모드에서 :1,$s/man/boy/g 를 실행하면 man 이 boy 로 교체될 것이다.

명령어의 맨 앞(1,$)은 교체 명령이 적용될 범위. 문서 전체에 교체 명령을 적용할 때는 %나 1,$를 사용. s는 교체 명령어이다. s 다음에 나오는 문자 하나는 교체 명령어에서 사용할 구분자가 되는데, 일반적으로 슬래시(/)를 사용한다. 하지만 다른 문자를 사용해도 상관없다. 예를 들어, 슬래시 대신에 쉼표를 구분자로 사용한다면 :1,$s,man,boy,g라고 적을 수 있다.

명령어 맨 뒤(g)의 옵션에는 i나 c를 사용할 수도 있다.
교체 명령 옵션

옵션|설명
---|---
g|범위 내에 검색된 모든(global) 문자열을 교체한다.
i|대소문자를 무시(ignore case)한다.
c|문자열을 교체하기 전 교체 여부를 확인(confirm)한다.
e|교체 과정 중 에러를 무시한다. 에러 메시지도 표지하지 않는다.

:%s/man/boy/c 라고 명령해 옵션에 c가 들어가면 문자열 교체 전에 교체 여부를 물어본다. 7가지 확인 입력을 선택할 수 있다. y는 yes(허용), n은 no(거부), a는 앞으로 남은 모든 교체를 실행, q는 교체 작업을 끝내고, l은 현재 행(line)의 교체 작업만 하고 교체 작업을 끝내고, ^E는 아래로 한 행을 스크롤 하여 보여주고, ^Y는 위로 한 행으로 스크롤 하여 보여준다.

- 교체 문자열에 구분자가 포함된 경우

이스케이프(escape)를 사용. 만약 횟수가 많아져서 가독성이 떨어지게 되면, 차라리 구분자를 다른 문자로 바꾸는 것을 추천.

> 특수문자 교체

> 정규 표현식으로 교체

위 두가지는 이해가 안되서 못함..

---

### 파일 관련 기능

파일에 관련된 기능을 중점으로 여러 파일 동시에 열기, 새로운 이름으로 저장하기 등의 방법을 살펴본다.

> 파일 열기

a.txt 파일의 10~20행을 복사해 b.txt 50행에 끼워 넣으려면 어떻게 할까??

보통 생각하는 방법으로 하면 문제가 있다. Vim을 종료했다가 다시 열었을 때 복사에 사용된 임시 버퍼인 레지스터의 내용이 유지되는지 알 수가 없다. (유닉스, 리눅스, 맥 OS X는 홈 디렉터리의 .viminfo 파일에 레지스터를 기록해둠.)

따라서 Vim을 종료하지 않고도 새로운 파일을 열어 작업하는 방법을 알아두는게 좋다.

- Vim 실행 중 다른 파일 열기

Vim에서 다른 파일을 여는 명령어는 :edit file이며, 다른 파일을 열기 전에 현재 파일을 수정하고 저장하지 않았다면 에러가 발생하니 주의해야 한다.

:edit b.txt 명령은 :e b.txt로 축약 가능.

여기까지 작업했다면 b.txt를 편집하고 있을텐데 여기서 \<CTRL-^\>를 눌러 이전 파일 사이를 오갈 수 있다. 이렇게 한번 열었던 파일을 다시 열 수 있는 이유는, Vim이 최근에 연 파일 목록을 기억하고 있기 때문이다. 

- 한꺼번에 여러 파일 열기

'vim clientlist.txt hello.c pibo.c'라고 명령하면 clientlist.txt가 열린 상태로 Vim이 시작하지만, 내부적으로는 세 파일이 목록에 등록된다. 이 상태에서 :n이나 :N 명령을 사용하면 파일 사이를 전환할 수 있다. 반복 횟수를 지정하여 :2n이라고 하면 두 번째 뒤의 파일로 이동한다.

파일 버퍼 관련 명령어

명령어|설명
---|---
:e[dit] 파일명|파일을 편집용으로 연다. 파일명을 모르는 경우 \<Tab\>을 누르면 현재 디렉터리의 파일을 하나씩 보여준다.
CTRL-^|이전 파일을 연다.
:e #|
:[#]n|여러 파일이 열려 있을 때, 다음 파일로 이동한다. #에 숫자를 넣으면 해당 숫자만큼 반복한다.
:[#]N|:n의 반대 방향으로 이동한다.

- 여러 파일 닫기

:qa 사용.

> 다양한 파일 저장법

명령어|설명
---|---
:w filename|파일을 저장(write)한다.
:sav filename|현재 파일을 다른 이름으로 저장(save as)한다.
:up|변경 사항(update)이 있는 경우에만 저장한다.
:x|Vim을 종료하면서 변경 사항이 있는 경우에는 저장한다.(일반 모드에서는 ZZ)

> 창 분할

- 창 수평 분할하기

:sp 명령은 현재 열려 있는 파일을 두 개의 창으로 나누어 보여주므로, 한 파일 내에서 서로 다른 위치를 볼 때 유용합니다. 단축키로 하고자 한다면 \<CTRL-W\> s 이다.

다른 파일로 창을 분할하고 싶다면 :sp file 명령을 사용하면 된다. 기본적으로 새 창과 기존 창은 균등한 크기로 나뉘며, 새 창의 크기를 직접 지정하려면 sp 명령 앞에 크기를 넣으면 된다. 예를 들어 :10sp file 로 명령하면 새로 생성되는 창의 크기는 10행이 된다.

- 창 수직 분할하기

:vs 명령은 창을 수직(vertical)으로 분할한다. 수평 분할과 마찬가지로 :vs file로 명령하면 다른 파일을 분할 창에 열어준다. 수직 분할도 명령어 앞에 숫자를 넣어 열 크기를 지정할 수 있다. 그리고 수직 분할의 단축키는 \<CTRL-W\> v 이다.

- 분할된 창 닫기

:q 명령으로 각각 닫기. 만일 한꺼번에 전부 닫고 싶다면 :qa 라는 명령어 사용.

- 복합 분할

창 사이를 이동하는 명령어

명령어|설명
---|---
CTRL-W CTRL-방향키|CTRL-W 방향키	방향키에는 h, j, k, l 이나 화살표 키를 사용할 수 있다.
CTRL-W CTRL-W|CTRL-W w	현재 창에서 오른쪽 방향으로 이동. 오른쪽 끝 창이라면 아래로 내려간다.
CTRL-W CTRL-P|CTRL-W p	바로 이전에 사용한 창으로 이동한다.

- 여러 파일을 분할된 창에 열기

Vim을 시작하면서 여러 파일을 분할된 창에 열고 싶다면 -o 옵션을 사용하면 된다. 예를 들어 다음 명령은 두 창을 상하로 분리한 후 위쪽 창에 hello.c를, 아래쪽 창에 pibo.c를 열어준다.

```
vim -o hello.c pibo.c
```

소문자 -o 대신에 대문자 -O를 사용하면 창을 좌우로 분할한다.

- 창 크기 조절하기

명령어|설명
---|---
CTRL-W =|모든 창의 크기를 동일하게 조절한다.
CTRL-W [#]+|# 크기만큼 크기를 키운다. #을 생략하면 1을 줄인다.
CTRL-W [#]-|# 크기만큼 크기를 줄인다. #을 생략하면 1을 줄인다.

- 파일 내용 비교하기

창 분할에는 특별한 기능이 있다. 바로 두 파일을 비교하는 창 기능이다. Vim을 시작할 때 -d 옵션을 사용하여 vim -d file1 file2 처럼 명령하면, file1과 file2를 수직 창 분할로 열면서 내용이 서로 다른 부분을 강조하여 표시해준다.

여기서 커서를 다른 행으로 이동하면 두 화면이 함께 움직이기 때문에 편리하다. 또한 다른 점을 비교한 후, 다른 점을 가져오는 기능(do)과 다른 점을 복사해 넣는 기능(dp)도 사용할 수 있다. 자세한 것은 도움말을 참고.

> 탭 페이지

창 분할 기능은 분할할 때마다 편집 화면이 반으로 줄어든다는 단점이 있다.

- 탭으로 열기

:tabedit hello.c 라고 명령하면 탭으로 열리는 것을 확인할 수 있다.

- 탭 사이 이동

:tabprevious 명령은 이전(previous) 탭으로 이동한다. 여기서 다음(next) 탭으로 이동하는 명령이 :tabnext 일 것이라 추측할 수 있다.

단축 명령 :tabn, :tabp 나 \<CTRL-PageDown\>, \<CTRL-PageUp\> 이 더 많이 쓰인다. 주의할 점은 몇명 터미널은 이미 스크롤다운, 스크롤업으로 예약되어 제대로 동작하지 않을 수 있다. (내 것에서 작동 안되는 듯)

탭 이동 명령

명령어|설명
---|---
:[#]tabn[ext]|다음 탭으로 이동하며, 일반모드의 gt와 동일하다.
[#]gt|#에 숫자를 지정하면 탭 번호가 지정된다.
:[#]tabp[revious]|이전 탭으로 이동하며, 일반모드의 gT와 동일하다.
[#]gT|#에 숫자를 지정하면 반복수가 지정된다.
:tabm[ove][#]|#번째 탭으로 현재 탭을 이동시킨다.(0부터 시작), #이 생략되면 가장 오른쪽으로 이동시킨다.

- 탭 열고 닫기

명령어|설명
---|---
:[#]tabe[dit] filename|#번째 탭에 파일을 연다. #을 생략하면 현재 탭 뒤에 생성된다. 번호는 0번 부터 시작한다.
:[#]tabnew filename|#번째 위치에 비어있는 탭을 만든다.
:[#]tabc[lose]|#번째 탭을 닫는다. #을 생략하면 현재 탭을 닫는다.

Vim시작시 여러 파일을 탭으로 열고 싶은 경우에는 -p 옵션으로 시작.
```
vim -p clientlist.txt hello.c
```

> 디렉터리 탐색

윈도우의 탐색기처럼 Vim 에도 디렉터리 리스트를 보면서 파일을 선택할 수 있는 netrw 라는 기능이 있다. 이 기능은 간단히 :e directory로 실행하면 된다.

예를 들어 :e . 명령은 현재 디렉터리를 탐색기처럼 열어준다.(vim을 시작할 때 vim. 명령을 사용해도 동일하다.)

- 파일 목록 이동하기

파일 사이를 이동할 때는 w나 b를 이용한다. 여기서 w는 word forword, b는 word backword의 의미이다. 물론 위아래 화살표 키나 방향 키(j 혹은 k)를 사용해도 된다.
그리고 파일을 열 땐 파일명 위에 커서를 두고 \<Enter\>를 누른다. 또한 화면 위쪽의 'Sorted by ...' 부분에서 \<Enter\>를 누르면 name, time, size 순으로 정렬 기준이 변경된다.

netrw의 주요 단축키

명령어|설명
---|---
\<Enter\>|파일을 현재 창에 열어준다.
i|파일 표시 방법을 변경(한 줄, 파일 정보도 함께, 와이드 형식, 트리 방식)한다.
s|정렬 방식을 바꿔준다.(이름순, 시간순, 크기순)
o|커서 위치의 파일을 수평 분할된 새 창으로 열어준다.
v|커서 위치의 파일을 수직 분할된 새 창으로 열어준다.
p|커서 위치의 파일을 미리보기 창으로 열어준다.(미리보기 창닫기는 \<CTRL-W\> z 나 :place를 사용한다.)
P|커서 위치의 파일을 바로 이전에 생성한 창에 열어준다. 바로 이전에 생성한 창이 없다면 수평 분할된 새 창으로 열어준다.
R|파일명을 바꾼다.
t|새로운 탭으로 분할하여 열어준다.
-|상위 디렉터리로 이동한다.


> 파일 열기(고급)

- 버퍼(파일) 목록 보기

우선 파일을 여러 개 열고 :ls 나 :buffers 혹은 :files라고 명령해 본다. 

*Vim의 버퍼(buffer)*

Vim에서는 편집 중인 문서를 버퍼(buffer)라고 부르며, 문서를 불러와서 보거나 작업하는 기억장치라는 의미로 사용된다. 버퍼가 특정 파일과 연결되어 있는 상태에서 불러오거나 저장되는 경우라면 '버퍼=파일' 이라고 말해도 큰 무리가 없지만, 빈 문서로 만들어진 경우라면 아직 파일과 연결된 상태가 아니므로 파일이라고 부를 수 없다. 그래서 파일명이 있든 없든 작업하는 문서를 가리켜 버퍼라고 한다. Vim 매뉴얼을 읽을 때도 상황에 따라서 버퍼가 문서임을 알아두면 이해하기 쉬울 것이다.

Vim은 종료하기 전까지 한 번이라도 열었던 파일의 목록을 모두 유지하고 있다.(중복해서 열었던 파일은 한 번만 추가된다.) 

버퍼 목록에 표시되는 기호

명령어|설명
---|---
%|현재 편집 중인 버퍼
#|바로 이전에 열었던 버퍼 혹은 다음에 열도록 예비된 버퍼. \<CTRL-^\>를 누르면 #이 표시된 파일이 열린다.
a|활성된 버퍼(현재 화면에 보이는 버퍼). 창 분할 기능을 쓰는 경우에는 여러 파일에 a 표시가 나타난다.
+|변경된 부분이 있는 버퍼

- 버퍼 목록에 파일 추가하기

일반적으로 버퍼 목록은 열었던 파일들을 자동으로 추가하여 작성된다. 하지만 열지 않았던 파일도 수동으로 목록에 추가할 수 있다. 사용법은 :n {pattern}으로, 앞에서 이미 다뤘던 :n 명령의 확장된 방법이다. 

예를 들어 :n \*.txt라고 하면 현재 디렉터리에서 \*.txt에 해당하는 모든 파일을 찾아서 목록에 추가한 후, 첫 번째로 검색된 파일을 열어준다. 여기에 하위 디렉터리를 검색하는 기능을 추가하고 싶을 때는 \*\*를 붙여서 :n \*\*/\*.txt라고 명령하면 된다. 이를 활용해 :n doc\*\*/\*.txt라고 하면 doc로 시작하는 디렉터리에 대해서만 검색할 수도 있다.

버퍼 관련 명령어들

명령어|설명
---|---
:ls|파일 목록을 확인한다.
:buffers|
:files|
:n {pattern}|지정된 pattern으로 파일을 검색하여 목록에 추가하고 첫 번째 검색된 파일을 열어준다.
{N}CTRL-^|{N} 번째 파일 목록을 연다.
:e #{N}|
:Of|현재 버퍼를 목록에서 제거한다. 연결된 파일이 있다면 해제하여 [No Name]버퍼로 만든다.
:r[ead] file|파일을 끼워 넣는다.

- 본문에 등장한 파일명 인식하여 열기

명령어|설명
---|---
gf|커서 위치의 파일명을 인식해서 열어준다.
\<CTRL-W\> f|커서 위치의 파일명을 분할된 창에 열어준다.
\<CTRL-W\> gf|커서 위치의 파일명을 탭에 열어준다.

gf는 디렉터리가 포함된 경우 경로 전체를 인식할 수 있으며, 경로가 없고 파일명만 있는 경우에는 현재 디렉터리와 path 옵션에 설정된 디렉터리를 순서대로 검색한다.

*Tip*

유닉스 계열의 Vim에서는 path에 시스템 헤더 디렉터리가 기본으로 포함되어 있으므로 C언어 헤더를 검색할 수 있다. 예를 들어 C언어 소스코드의 #include \<stdio.h\> 가 있다면 stdio.h 위에 커서를 두고 gf를 누르면 시스템 헤더 파일을 찾아서 열어준다. 
만일 사용자가 검색 대상 디렉터리를 추가하고 싶다면 path에 추가하면 된다. 예를 들어 ~/doc을 추가하고 싶다면 :set path+=~/doc라고 명령하면 된다. 자주쓰이는 파일들이 있다면 설정 파일인 .vimrc에 경로를 추가해두면 편리하겠지??

> 파일 인코딩

지금부터는 파일을 저장하는 문자 세트(character set)에 대한 이야기이다. 영문 뿐 아니라 한글, 중국어, 일본어, 심볼 같은 다양한 문자를 사용하는 경우라면 필수로 알아야겠지만, 영문만 사용하는 경우라면 몰라도 크게 문제가 없다.

파일 인코딩이란 파일에서 사용하는 문자 형식을 의미한다. 대표적으로 영문 기호를 표시하는 ASCII, 한글을 표현할 수 있는 EUC-KR 그리고 여러 언어와 기호를 표현할 수 있는 유니코드 등이 있다. 텍스트 파일을 열 때는 정해진 인코딩 형식으로 읽어야만 내용을 제대로 볼 수 있다. 만약 한글을 UTF-8로 인코딩한 텍스트 파일을 ASCII로 읽어버리면 문자들이 깨져 보이게 된다.

- 인코딩 읽기 옵션

사용자가 자신이 주로 사용하는 인코딩 방식을 Vim의 fileencodings 옵션에 넣어두면, Vim이 이 방식들을 차례대로 테스트하면서 파일을 해석하려고 시도한다. 참고로 옵션 이름이 길기 때문에 약어인 fencs를 더 많이 사용.

ucs-bom은 유니코드의 한 형태이며, 저장할 때 사용한 바이트 순서(Byte Order Mark, BOM)를 구별한다. 널리 사용되는 utf-8은 BOM을 사용하지 않지만, 이 외의 유니코드들은 BOM을 체크해야만 데이터를 읽을 수 있기 때문에 이를 먼저 체크하는 것이 좋다.

*Note* *유니코드와 BOM*

유니코드는 CPU구조에 따라 빅 엔디안(Big endian) 혹은 리틀 엔디안(Little endian) 형식으로 저장될 수 있으므로, 파일 앞부분에 해당 파일이 어떤 형식으로 저장되었는지를 구별하는 특별한 문자열을 넣을 수 있다. 이때 엔디안 바이트 순서를 확인하기 위한 문자열을 BOM이라고 한다.

- 기본 인코딩 형식 설정하기와 현재 인코딩 형식 확인하기

Vim은 파일을 읽은 후 fileencoding 옵션(s가 없음에 유의)에 현재 파일을 읽을 때 사용했던 인코딩을 저장해 둔다. 보통은 줄임 표현인 fenc를 사용한다. 따라서 
```
:set fenc
```
라고 명령하면 현재 파일의 인코딩 형식을 보여준다.

- 파일 인코딩 형식

fenc 옵션은 현재 파일의 인코딩 형식을 변경할 때도 사용된다. 예를 들어 현재 파일의 fenc를 확인해보니 euc-kr 인데, :set fenc-utf-8이라고 명령한 후 저장하면 utf-8로 변환되어 저장된다. 반대로 명령하면 utf-8로 작성된 문서를 euc-kr로 바꿀 수도 있다. 하지만, 캐릭터 정보가 많은 형식(utf-8)에서 상대적으로 적은 형식(euc-kr)으로 바꾸면 일부 캐릭터 정보가 사라질 수도 있다는 점 유의!

---

### 편리한 편집 기술

> 단어와 문장 사이를 이동하기

- 단어나 특별한 경계로 움직이기

명령어|설명
---|---
0|0번째 열
^|공백을 제외한 행의 시작 부분
$|마지막 열(행의 끝)
w|단어의 시작 위치 혹은 문장부호의 경계를 따라서 이동한다.(words forward)
e|w와 같으나, 단어의 끝 부분에 위치한다.(end of word)
b|w와 비슷하나 진행 방향이 역방향이다.(words backward)
W, E, B|w, e, b와 비슷하지만 단어가 가진 의미를 따져서 이동. 예를 들어 '/usr/local/bin'이라는 문자열을 만났을 때 w, e, b는 슬래시(/)나 슬래시 바로 뒤에 있는 문자를 분장부호로 인식하지만, W, E, B는 경로 전체를 단어로 인식한다.

일반모드에서 명령어 앞의 숫자는 반복 횟수. 3w라고 명령하면 어떻게 될까?? 

- 괄호나 문단, 블록 단위 이동

프로그래밍을 하는 사람에게는 커서가 위치한 괄호와 짝을 이루는 괄호를 찾는 %가 매우 유용하다. 만일 커서의 위치가 괄호가 아니라면 가장 근접한 괄호로 이동한다. 인식하는 괄호의 형태는 (), {}, [] 이다. 이 외에 문장, 문단, 블록 단위로 이동하는 기능도 있다.

명령어|설명
---|---
%|가장 가까운 괄호 짝으로 이동
(,)|문장 단위의 시작 위치, 끝 위치로 이동
{,}|문단 단위의 시작 위치, 끝 위치로 이동
[[,]]|블록 단위의 시작 위치, 끝 위치로 이동

*Note* *Vim 7.x의 괄호 표시 기능*

참고로 Vim7.x 버전에서는 커서가 괄호에 위치하면 짝이 되는 괄호를 밝게 표시해주는 기능이 생겼기 때문에, 굳이 %를 누르지 않아도 짝이 되는 괄호를 쉽게 알 수 있다.

> 오퍼레이션 펜딩 모드

고급 기능을 배우는 데 필수적인 오퍼레이션 펜딩 모드(operation pending mode)를 보자. 오퍼레이션 펜딩 모드는 새로운 모드라기보다는 일반 모드의 기능 중 명령어가 지연되는 방식을 의미한다.

- 오퍼레이션 펜딩 모드란?

예를 들어 일반 모드에서 $와 d$의 차이점을 생각해보자. $는 커서를 행 끝으로 이동시키는 명령어고, d$는 현재 커서 위치부터 행의 끝까지를 삭제하는 명령어이다. 여기서 $는 키를 누르면 즉시 실행되지만, d$는 d를 누른 다음 $를 누르기까지 아무 작동도 하지 않는다. 즉 d 명령이 실행되기는 하지만 뒤따라오는 추가 명령어가 입력되기까지는 대기 상태(pending)에 머무른다는 말이다. 이렇게 다른 명령어를 받기 위해 대기하는 상태를 오퍼레이션 펜딩모드라고 한다.

- 범위 지정하기

Vim의 도움말을 보면 오퍼레이션 펜딩 모드에 추가로 입력되는 키 중{motion}이라고 부르는 것들이 종종 등장하는데, 이는 단어 사이나 행, 특정 위치로 이동하는 키 입력을 가리키며, 이때 입력된 이동 범위가 명령어가 작동할 범위가 된다.

{motion}을 사용하는 명령어의 예

명령어|설명
---|---
y{motion}|{motion}만큼 복사
d{motion}|{motion}만큼 삭제
c{motion}|{motion}만큼 변경(삭제 후 입력 모드로 전환)

이렇게 오퍼레이션 펜딩 모드를 알아야 하는 이유는 나중에 단축키나 자동화를 배울 때 오퍼레이션 펜딩 모드에 따라 다양한 기능을 구현할 수 있기 때문이다.

*Tip* *커서 위치의 단어를 선택하는 {motion}*

dw 명령으로 단어 하나를 온전히 삭제하려면 커서의 위치가 단어의 시작 부분이어야 하는 단점이 있다. 이런 단점을 보완하여 커서 위치가 어디든 상관 없이 단어 전체를 삭제 범위로 지정할 수 있는 ai와 iw 명령이 존재한다.
이들은 오퍼레이션 펜딩 모드로 작동하는 다른 명령어와 결합하여 daw, diw, caw, ciw 처럼 사용된다. 차이점은, aw가 단어의 앞뒤 공백을 포함하는 반면, iw는 공백을 포함하지 않는다는 점이다. 단 aw의 공백은 문맥에 따라서 앞부분일 수도 있고 뒷부분일 수도 있다.

> 약어 매크로

약어(abbreviation) 매크로는 입력 모드나 명령행 모드에서 길고 복잡한 문장을 짧은 단어로 대체하여 입력할 수 있는 기능이다.

'내메일' 이라고 입력하면 colin7street@naver.com 이 입력되게 하고 싶다.
입력 모드에서 '시간()'이라고 입력하면 현재 날짜와 시간이 입력되게 하고 싶다. 등등...

이 기능들을 구현하려면 .vimrc 파일에 코드를 넣어두면 된다.

```
ab 내메일	colin7street@naver.com
ia 시간0	<C-R>=strftime("%y.%m.%d-%H:%M:%S")<CR>
```

이 때 억지로 약어를 변환하고 싶다면 \<CTRL-]\>를 사용하면 된다. 반대로 약어로 해석되기를 원하지 않는다면 \<CTRL-V\>를 누르면 된다.

3행과 4행의 ia는 입력 모드에서만 작동하는 약어이다. 그리고 입력 모드에서 \<C-R\>은 레지스터(register) 버퍼를 붙여 넣는 단축키이며 다음에 나오는 =는 레지스터 이름이 된다. = 레지스터는 특수 키나 함수 같은 기능을 호출할 때 주로 사용하는데 여기서는 현재 시간을 출력하는 Vim 내장 스크립트 함수인 strftime을 호출하는데 사용되었다.
더 자세한 함수 설명은 고급 서적을 통해 배우도록!

- 약어 설정과 해제

명령어|설명
---|---
:ab[lhs]|현재 설정된 모든 약어 목록을 출력한다. lhs에 약어를 지정하면 해당 약어의 정보만 출력.
:ab{lhs}{rhs}|약어 lhs를 rhs로 설정한다.
:unab{lhs}|약어 lhs를 해제한다.
:abclear|설정된 모든 약어를 해제한다.
:la{lhs}{rhs}|ab와 기능은 같지만 입력 모드에서만 작동.
:ca{lhs}{rhs}|ab와 기능은 같지만 명령행 모드에서만 작동.

이 중 명령행 모드에서만 작동하는 ca는 여러모로 쓸모가 있다. 예를 들어 :w 나 :wq를 잘못 입력해 :ㅈ, :ㅈㅂ 이 입력되었을 때 이를 자동으로 변환해준다.
```
ca ㅈ w
ca ㅈㅂ wq
```

*Tip* *한글이 포함된 약어 매크로가 작동하지 않는다면*

간혹 한글이 포함된 약어가 제대로 작동하지 않는 경우가 있다. 이는 .vimrc 파일과 편집하는 문서 파일의 인코딩 형식(fileencoding)이 일치하지 않을 때이다.  이런 문제를 해결하려면 설정 파일과 편집할 파일의 fileencoding을 통일시켜야만 한다.

> 레지스터 활용하기

- 편집 관련 레지스터

레지스터 이름|설명
---|---
""|가장 최근에 복사, 삭제된 데이터
"0|가장 최근에 복사(yank)된 데이터
"1~"9|가장 최근에 삭제된 데이터(시간순, 1번이 가장 최근 데이터)

- 기능 관련 레지스터

레지스터 이름|설명
---|---
"-|가장 최근에 한 라인 이내로 삭제한 데이터
"/|가장 최근에 검색한 데이터
":|가장 최근에 명령행 모드에서 내린 명령어 데이터(읽기 전용)
".|가장 최근에 입력한 데이터(읽기 전용)

- 파일 관련 레지스터

레지스터 이름|설명
---|---
"%|현재 편집 중인 파일명(읽기 전용)
"#|이전에 열었던 파일명 \<CTRL-^\>을 누르면 열게 될 파일. (읽기 전용)

- 사용자 등록 레지스터

영문자는 사용자가 임의로 등록할 수 있는 레지스터이다. 그런데 레지스터 이름에 소문자를 쓰는 경우와 대문자를 쓰는 경우가 다르기 때문에 주의해야 한다.

- 레지스터 복사, 삭제, 붙여넣기

명령어|설명
---|---
"{reg}y{motion}|{reg} 레지스터에 {motion}에 해당하는 부분을 복사한다.
"{reg}p|{reg} 레지스터의 내용을 현재 커서 뒷부분에 넣는다. (레지스터에 개행 문자가 포함된 경우는 커서의 아래 행에 넣는다.)
"{reg}P|{reg} 레지스터의 내용을 현재 커서의 앞부분에 넣는다. (레지스터에 개행 문자가 포함된 경우는 커서의 윗 행에 넣는다.)
"{reg}d{motion}|{reg} 레지스터에 {motion}에 해당하는 부분을 잘라 넣는다. (Vim에서 삭제하는 모든 행위는 잘라내기로 작동한다.)
CTRL-R{reg}|입력 모드에서만 사용하는 명령으로 {reg} 레지스터를 붙여 넣는다. "{reg}를 생략하면"" 레지스터를 가리킨다.

참고로 레지스터 내용은 .viminfo 파일에 저장되므로, Vim을 종료한 뒤에 다시 실행해도 레지스터를 사용할 수 있다. (윈도우 Vim은 \_viminfo 파일을 사용)

---

### 자동화

>

일반asdf;lkjdjshow me the money.dlack sheep walll, food for thoughtdf..god bless youf...

