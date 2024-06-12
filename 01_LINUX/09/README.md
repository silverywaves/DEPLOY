# 변수
### 변수란 
```
  변수 : 변하는 수(값)
  변수지정 : 변수를 지정할 '공간 설정'
```

<br>

### 변수 규칙
 ```
1.형태 : 이름=값

linux=easy

2. 값의 내용을 그대로 출력할 때는 'echo $' 사용한다

echo $linux

3.값은 기본적으로 문자열 으로 인식한다

a=1111		- 1111을 문자열 취급
b=1+1		- 1+1을 문자열 취급
c="test"	- "test"를 문자열 취급
d=test		- test를 문자열 취급


4.'이름'과 '=' 과 '값' 사이는 공백을 두지않는다.

hello = itbank (x)

5. $ 는 변수 내의 명령어나 스크립트 결과를  출력할때 사용되는 특수문자이다.
(변수 값 문자열 출력은 echo $, 변수 내 명령어에 의한 결과 출력은 $)


6. ' '(홑따옴표)는  명령어나 스크립트 처리 결과를 변수에 저장

hi='ls -al'
$hi


7. 변수의 연산은 'expr' 라는 스크립터 프로그램을 이용한다

x='expr1 + 2'		expr , 1 , + , 2 사이는 각각 띄어준다
$x
```

<br>

### 쉘 연산자 기호
```
1 + 1		2 (덧셈)   

4 - 1		3 (뺄셈) 

3 \* 2 		6 (곱셈; 곱셈의 경우에는 *앞에 \(원화표시)을 붙여줘야 한다) 

6 / 2		2 (나눗셈의 몫)

6 % 2		0 (나눗셈의 나머지) 

3 = 2		0 (항등관계 비교: 참이면 1, 거짓이면 0)

3 != 2		1 (비등관계 비교: 참이면 1, 거짓이면 0)

3  > 2, 3 < 2	1, 0 (대소관계 비교: 참이면 1, 거짓이면 0)

3 >= 3, 2 <= 3	1, 1 (크거나 같음, 작거나 같음)
```

<br>

#### 미니 문제
> 1.
```
변수 a 지정하고 변수안에 'A man has to have a code,' 값을 넣으세요
변수 b 지정하고 변수안에 'a way of life to live by.' 값을 넣으세요
```

<details>
  <summary>답</summary>

```

```

</details>

> 2.
```
변수 a 의 값을 출력하세요
변수 b 의 값을 출력하세요
변수 a,b 값을 동시에 출력하세요
```

<details>
  <summary>답</summary>

```

```

</details>

> 3.
```
변수 c 지정하고 변수 c 실행시 /test 디렉토리가 생성되도록하세요
변수 d 지정하고 변수 d 실행시 /test 안에 testfile 이 생성되도록하세요
변수 e 지정하고 변수 e 실행시 /test 의 목록이 출력 되도록 하세요
```

<details>
  <summary>답</summary>

```

```

</details>

> 4.
```
변수 f 지정하고 변수 f 실행시 1 + 4 연산을 하도록 하세요
변수 g 지정하고 변수 g 실행시 10 - 4 연산을 하도록 하세요
```

<details>
  <summary>답</summary>

```

```

</details>

<br>

### 변수 종류(적용되는 범위에 따라)
> 지역변수 : 계정별 따로 적용 (서브쉘 x)
```		
지정 : itbank=“heath”	 
확인 : echo $itbank	 
해제 : unset itbank	
```

<br>

> 전역변수 : 전체계정에 적용( 서브쉘 o)	ex)PATH, HOME
```		
지정 : export ITBANK=“heath”	
확인 : echo $ITBANK
해제 : unset ITBANK
```

<br>

> cf) 
```
set 	:모든변수 확인 명령어(지역변수 + 전역변수 + 환경변수)
env	:환경변수 확인 명령어
```

<br>

### 환경변수 종류 :사전에 의미가 정해진 전역변수
> 프로필 파일에 정의되어있다
```
HISTFILE	: 히스토리(History) 파일의 절대 경로
HISTSIZE	: 히스토리 파일에 저장되는 명령어의 개수(줄기준)
HISTFILESIZE	: 히스토리 파일의 파일 크기
HOME		: 사용자 홈 디렉토리의 절대 경로
HOSTNAME	: 시스템의 호스트명
LANG		: 쉘 사용 시 기본으로 지원되는 언어
LOGNAME		: 사용자 계정 이름
MAIL		: 도착한 메일이 저장되는 경로
PATH		: 명령을 탐색할 경로
PS1		: 1차 프롬프트 변수
PS2		: 2차 프롬프트 변수(명령어 대상 경로를 계속 추가해서 적용시 사용 )
CDPATH		: cd 명령 사용시 인자로 주어진 디렉토리를 찾을 경로
PWD		: 작업 디렉토리 절대 경로
SHELL		: 로그인 쉘 
TERM		: 로그인한 터미널 종류
UID		: 사용자의 UID
USER		: 사용자의 이름
```

<br>

### 주요 프롬프트 형식
```
\d		: '요일 월 일' 형태로 날짜를 표시(ex "Wed jan 15")
\h		: 호스트 이름
\s		: 사용 중인 쉘의 이름
\t		: 24시 형태의 현재 시간(ex , HH:MM:SS)
\T		: 12시 형태의 현재 시간(ex , HH:MM:SS)
\@		: 12시 형태의 현재 시간에 AM/PM을 추가로 표시
\u		: 현재 사용자의 이름
\w		: 현재 작업 디렉토리(홈 디렉토리의 위치를 ~로 표시)
\W		: 현재 작업 디렉토리 중 마지막 디렉토리만 표시
\!		: 현재 명령의 히스토리 번호
\\		: \를 표시
```

<br>

#### 환경변수 실습
> [예제-1 모든 계정 History 기능 사용하기]
```
echo $HISTFILE
/root/.bash_history

echo $HISTFILESIZE
0

echo $HISTSIZE
0


touch /etc/skel/.bash_history	-->스컬경로 history 파일생성
HISTFILESIZE=1000		-->히스토리 파일 사이즈 1000설정
vi /etc/profile
HISTSIZE=1000
:wq

useradd user1			--> user1 생성

user1 로그인 -> 명령어 입력 -> 로그아웃(exit) 후 재 로그인 ->.bash_history 파일 내 기록 확인
```

<br>

> [예제-2 PATH 환경변수에 경로 추가]
```
mkdir /newbin
cp /bin/ls  /newbin/newls
cp /bin/pwd /newbin/newpwd

PATH=$PATH:/newbin
echo $PATH --마지막에 /newbin 추가 확인

newls -al /etc 	--명령어 사용확인
```

<br>

> [예제-3 CDPATH 환경변수에 경로 추가]
```
mkdir -p /cdpath1/a /cdpath2/b

CDPATH=/cdpath1:/cdpath2

echo $CDPATH	-- 경로확인

cd a 
/cdpath1/a

cd b
/cdpath2/b
```

<br>

> [예제-4 PS1환경변수를 이용해서 명령어 프롬프트 변경]
```
PS1='PStestCOMMAND>'
변경확인

PS1='\h>'

PS1='\u>'
```

<br>

#### [미니 문제]
```
1./b 디렉토리를 만들고 /bin/touch 명령어를 /b/t로 이름변경 복사하고
PATH환경변수에 추가해서 t 명령어를 사용하세요


2./cdtest1/test1 /cdtest2/test2  디렉토리를 만들고 CDPATH를 이용해서
test1, test2로 접근하세요


3.명령어 프롬프트의 모양을 '본인이름_COMMAND>'로 변경하세요
```

<br>

#### 연습문제
```
1.전체 계정에 이전 명령어 불러오기 기능을 해제하세요

2.user1 계정만 이전 명령어 불러오기 기능을 활성화 시키세요

3.user2 계정만 이전 명령어 불러오기 기능을 활성화 시킨 후 이전 명령어 내용을 저장하도록 하세요 

4.user3 계정만 메일함을 /user3only/user3 으로 설정하고 권한부여하세요

5. 새 명령어 경로 /execute를 만들고 PATH 환경변수에 경로 추가해서 c,m,l 이라는 키를 누르면

각각 cp , mkdir , ls 이라는 명령어가 적용 되도록 하세요

6. user1 계정의 홈디렉토리에 user1path 디렉토리 생성 후 user1 이라는 명령어를 사용하면
cat 명령어가 실행되도록 하세요

7. user2 계정의 명령어 프롬프트를 USER2_COMMAND> 로 수정하세요

8. user3 계정의 보조 프롬프트를 ★로 수정하세요

9. 모든계정에서 cd 명령어를 이용하면 /testdir의 경로가 기본으로 설정되도록하세요

10. user1 계정에서 cd 명령어를 이용하면 홈디렉토리의 경로가 기본으로 설정되도록하세요
```

<br>

