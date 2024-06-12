# 쉘
쉘 기본
--- 
### 쉘
```
리눅스에서 사용하는 중간 언어
사용자의 명령어를 커널에 전달해 주는 역할

사용자 	->	쉘	->	커널	-> 	하드웨어
	명령어	번역	기계어	인식	동작
```

<br>

### 쉘 역할

1) 명령어 해석

2) 프로그래밍

3) 계정의 프로필 설정(쉘문법 + 변수)

```
  cf)
  프로필? 계정의 작업환경
```

<br>

### 쉘종류
|종류|설명|
|-|-|
|본쉘(sh)|커널 기본쉘(초기쉘, 단순,속도빠름)<br>시스템 관리작업 수행하는 쉘스크립트에서 사용|
|콘쉘(ksh)|유닉스 기본쉘 , 히스토리, alias제공, 본쉘과 호환|
|C쉘(csh)|안드로이드 사용 본쉘기능확장(alias,히스토리추가)<br>쉘 스크립트 구문형식이 c언어와 같아서 c쉘|
|배쉬쉘(bash)|리눅스 기본쉘, 본쉘 호환 , Ksh + c쉘 콘쉘 기능 포함|
|TCsh|c쉘기능 확장,(명령행 편집, 명령어 완성기능, 히스토리 목록에서의 시간표시기능)|
|Dash|데비안 계열 기본쉘|
|Nologin쉘|root가 아닌 사용자들의 시스템 접속을 막는 프로그램 |

<br>

### 실습
```
  ex) test1 계정 접속 금지
  
  vi /etc/passwd
  쉘지정경로 -> /sbin/nologin 로 변경 
  :wq
  test1 로그인 시도 ....실패
```

<br>

### 쉘 확인
```
  echo $SHELL			- 로그인 쉘 확인
  cat /etc/passwd |grep root	- /etc/passwd  확인
  cat /etc/shells			- OS 에 적용가능 쉘 확인
  bash --version 			- 쉘 정보 자세히 보기
```

<br>

### 쉘 변경
> [영구변경-로그인 쉘 적용]
```
  yum install -y ksh ksh tcsh	-- 쉘 다운로드 	
  
  chsh	 			-- 쉘 변경 명령어
  chsh -s /bin/ksh	
  		
  echo $SHELL			-- 로그인 후 적용	
  
  cat /etc/passwd |grep root	
```

<br>

> [임시변경-서브 쉘 적용]
```
  ksh,tcsh	
```

<br>

> 참고
```
  로그인 쉘 	: 로그인시 적용되는 쉘
  서브 쉘 	: 로그인 상태에서 다른 쉘로 변경시 적용되는 쉘
```

<br>

# 프로필
### 프로필 개념
```
  각 사용자 계정의 작업환경
```

> 프로필환경의 구성
```
  쉘(명령어해석기)
  변수
  문법(코드)
```

<br>

### 프로필 설정 파일	
> 로그인쉘
```
  1)/etc/profile 	  : 전체계정 적용 프로필
  (로그인쉘 프로필)	
  
  2)~/.bash_profile : 개별계정 적용 프로필
  (로그인쉘 프로필)
```

> 서브쉘
```
  1)~/.bashrc	  : 개별계정 적용 프로필
  (서브쉘 프로필)	ex) alias 설정	
  			
  2)/etc/bashrc	  :전체적용 계정 프로필
  (서브쉘 프로필)
```

<br>

### 프로필 환경 설정 파일 동작 순서
> 계정로그인시 
```
  /etc/profile -> ~/.bash_profile -> ~/.bashrc	-> /etc/bashrc
```

<br>

### 로그인쉘 실습

> 환경
```
  user1,user2,user3 계정 추가(패스워드 1)
  vi /etc/profile -> HISTSIZE=0
  vi ~user1/.bash_profile -> HISTSIZE=0
  vi ~user2/.bash_profile -> HISTSIZE=0
  vi ~user3/.bash_profile -> HISTSIZE=0
```

> cf) HISTSIZE(환경변수) 사용 
```
  - 사용했던 명령어의 저장 줄수를 설정할수 있는 환경변수
  - 화살표를 이용해서 이전 명령어를 불러올수 있음
  - 환경변수란 : 모든사용자 계정에서 사용할 수 있는 변수 
```

<br>

#### [예제-1]  - /etc/profile

> 실습
```
vi /etc/profile 	
HISTSIZE=1000	-명령어 저장수 1000줄	 
:wq
```

> 확인
```
user1,user2,user3 로그인 HISTSIZE 적용확인

vi /etc/profile
HISTSIZE=0
:wq
```

<br>

#### [예제-2] ~/.bash_profile
> 실습
```
vi ~user1/.bash_profile
HISTSIZE=1000
:wq
```

> 확인
```
user1 ->HISTSIZE 적용o
user2 ->HISTSIZE 적용x
user3 ->HISTSIZE 적용x
```

<br>

### 서브쉘 실습

> [환경] - alias사용
```
test1,test2,test3 생성
alias t='touch ~/subshelltest'
su(Substitute User) : 사용자 전환 명령어 
su itbank or su heath 
```

<br>

#### [예제-1] - /etc/bashrc
```
vi /etc/bashrc
alias t='touch ~/subshelltest'
:wq

su test1
t 엔터->ls -al ~/subshelltest 확인->존재 (확인 후 subshelltest파일 삭제해주세요)
exit
su test2
t 엔터 ->ls -al ~/subshelltest 확인->존재(확인 후 subshelltest파일 삭제해주세요)
exit


vi /etc/bashrc
alias t='touch ~/subshelltest' 삭제
:wq
```

<br>

#### [예제-2]  - ~/.bashrc
> test2 계정만 alias적용
```
vi ~test2/.bashrc
alias t='touch ~/subshelltest'
:wq

su test1
t 엔터->ls -al ~/subshelltest 확인 -> x
exit
su test2
t 엔터 ->ls -al ~/subshelltest 확인 -> o
exit
```

<br>

#### 미니문제
```
  1.전체계정 로그인시 'hi' 를 입력하면  'welcome to Linux'가 출력되게 하세요
  
  2.user1 계정 로그인시 'go' 를 입력하면 'home!!'이 출력되게 하세요
  
  3.로그인 상태에서 다른 계정으로 전환시(su) 모든계정에서 'va'를 입력하면 'cation'이 출력되도록하세요
  
  4.모든 계정 로그인 상태에서 user1 계정 으로 전환시(su) 'u'를 입력하면 'This is user1 Account'가 출력되게 하세요
```

<details>
<summary>답</summary>

```

```

</details>

<br>

#### 연습문제
> 환경 
```
Useradd itbank 
Useradd heath
Useradd user1
passwd itbank
1
1
passwd heath
1
1
passwd user1
1
1
/etc/profile	에 HISTSIZE=0 설정
~/bash_profile 	에 HISTSIZE=0 설정
```

> 문제
```
1. 로그인 시 itbank만 HISTSIZE=1000이 적용되도록 설정
 
2. 사용자 전환 시 heath 계정에 HISTSIZE=1000이 적용되도록 설정

3. 전체 계정에 m키를 누르면 mkdir 명령어가 실행되도록 하세요

4. User1계정에서만 c 키를 누르면 cd 명령어가 적용되도록 하세요

5.Itbank 계정으로 전환 시 ok 를 누르면 go Home 이라는 문자가 뜨도록 하세요
```

<details>
<summary>답</summary>

```

```

</details>





