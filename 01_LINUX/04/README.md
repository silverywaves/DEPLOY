# 특수문자
논리 연산자
---
### && : and연산
> 왼쪽 명령어 성공시 오른쪽 명령어 실행<br>왼쪽 명령어 실패시 오른쪽 명령어 실행x

<details>
  <summary>실습</summary>

```
  mkdir /andtest && touch /andtest/testfile1
  ls -al /andtest 
  
  ls -al /fj0923k20  && touch /andtest/testfil2
  ls -al /andtest
```

</details>

<br>

### ||  : or 연산	
> 왼쪽 명령어 성공시 오른쪽 명령어 실행 x<br>왼쪽 명령어 실패시 오른쪽 명령어 실행

<details>
  <summary>실습</summary>

```
  mkdir /ortest || touch /ortest/testfile1
  ls -al /ortest
  
  
  ls -al /2m302903rk2 || touch /ortest/testfile2
  ls -al /ortest
```

</details>

<br>

#### [미니문제]
```
  기존 /andtest, /ortest 디렉토리를 삭제하고 진행 하세요
  
  1. /andtest 디렉토리를 만들고 그안에  and 파일을 만드는 작업을 한줄명령어로 수행하세요
  
  2. /ortest 디렉토리를 만들고 그안에 or파일을 만드는 작업을 한줄 명령어로 수행하세요 
```

<details>
  <summary>답</summary>

```

```

</details>

<br>

와일드카드
---
> 와일드 카드  : 여러개의 파일을 동시에 지정할 때 사용
```
  [환경]
  mkdir /test
  cd /test
  touch 1111 1112 1122 1222 2222 2221 2211 2111
  mkdir appp bppp cppp dppp eppp
```

<br>

### 1. * (모든문자, 길이상관x)
```
  ls -l *		디렉토리 내 모든문자
  ls -l 1*		처음이 1인 모든 문자
  ls -l 2*		처음이 2인 모든 문자
  ls -l *1		마지막이 1인 모든문자
  ls -l *1*		1을포함한 모든 문자
```

<br>

### 2. ? (모든문자, 물음표만큼의길이)
```
  ls -l ?		한문자인 파일&디렉토리 추력
  ls -l ????	4문자인 파일&디렉토리 출력
  ls -l ??11	마지막이 11인 네문자 출력
  ls -l ??2?	세번째가 1인 네문자 출력
  ls -l ?2*		첫번째 어떤 문자 상관x
  	 	두번째 2를 포함한 모든 문자
```

<br>

### 3. [] (범위지정)
```
  ls-l [abcde]*	첫마디가 a,b,c,d,e를 가진 모든문자
  ls-l [a-e]* 	첫마디가 a,b,c,d,e를 가진 모든문자
  ls-l [abc]*	첫마디가 a,b,c를가진 모든 문자
  ls-l [ac]*		비연속적문자가능		
```

<br>

#### [미니문제]
```
  /test 안에서 1을 포함한 파일&디렉토리의 목록을 출력하세요
  
  /test 안에서 앞글자가 1이고 끝글자가 2인 파일의 목록을 출력하세요
  
  /test안에서 첫마디의 범위가 a~c 까지인 모든 문자의 목록을 출력하세요
```

<details>
  <summary>답</summary>

```

```

</details>

<br>

리다이렉션 
---
> 표준입력&출력을 파일로 대체
```
  [환경]
  mkdir /retest
  cd /retest
```

<br>

### 1. 표준출력(>,>>)
> 모니터 출력물을 파일로 대체

#### 기본 확인
```
  Cat		
  hello	- 키보드 입력
  hello	- 모니터 출력
  컨트롤+c- 작업 취소
  
  Cat >a
  hello	- 키보드 입력
  	- 모니터 출력 없음
  컨트롤+c- 작업 취소		
  
  ls -l 	- a파일 생성
  
  cat a	- a파일 확인 hello가 저장
```

#### [>] : 생성,덮어쓰기
```
  cat a	- hello 저장
  
  cat  > a	 
  Test
  CTRL+C
  
  cat a	- test 저장
  
  cat > a  	
  heath
  CTRL + c
  
  cat  a	- heath 저장
```

#### [>>] : 생성,추가하기
```
  cat >> b
  bbb
  CTRL + c		
  
  ls -al 	- b파일 생성
  cat b	- b내용보기, bbb 저장
  
  cat b		
  cat >> b 		
  Aaa	
  CTRL + c
  
  cat b	- bbb아래에 Aaa 저장
  
  cat b		
  cat a b > c 	
  cat c		 
  tail -2  c>d	
```

<br>

### 2. 표준 입력(<)
> 키보드에 입력할 내용을 파일로 대체

### sort  : 정렬 명령어
```
  cat > a
  5
  3
  4
  2
  1
  
  ctrl +c
  
  sort < a
  1
  2
  3
  4
  5
```

<br>

### 3. 표준 에러(2>)
> 에러 메시지만 파일로 대체
```
  ls -al /23f2f3 
  ls -al /109k029 2> errfile1
  cat errfile
```

<br>

### 4. 표준 출력 & 표준에러 (&>)
> 출력물 + 에러메시지를 파일로 대체
```
  ls -al /etc/ /etwcmwioecw 2> errfile2
  ->/etc/목록은 출력, /etwcmwioecw 목록의 에러메시지는 파일로 저장
  
  ls -al /etc/ /eetwomf2030 &> errfile3
  ->/etc/의 목록과 /etwcmwioecw 목록의 에러메시지는 파일로 저장
```

<br>

### 미니문제
```
  [환경]
  mkdir /retest
  
  1. /etc안의 디렉토리의 목록을 /retest/a에 저장하세요
  2. /etc/passwd의 위에서 7번째 행까지의 내용을 /retest/b에 저장하세요
  3. /etc/inittab의 아래에서 4번째 행까지의 내용을 /retest/c에 저장하세요
  4. /retest 안의 a,b,c,의 내용을 병합하는 d 파일을 만드세요
```

<details>
  <summary>답</summary>

```

```

</details>

<br>

파일 디스크립터(File Discriptor,fd)
---
### 정의
- 리눅스의 일반파일, 장치파일을 포함한 모든 파일을 관리하는 방식.
- 리눅스에서 프로세스(여기선 명령어)가 파일에 접근할때 사용되는 개념
- 프로그램이 실행될때(프로세스상태) 기본적으로 할당되는 파일 스크립터가 존재(아래)
	- 표준입력장치 (키보드) fd/0 stdin
	- 표준출력장치 (모니터) fd/1 stdout
	- 표준에러장치 (모니터) fd/2 stderr

<br>

```
  [환경]
  mkdir /retest
  cd /retest
```

<br>

### 1. 표준출력 덮어쓰기	: 1>, > ( 1 은 생략가능)
> stdout(모니터로)을 파일로 방향지정
```
  cat 1> a
  test
  ctrl+c
```

<br>

### 2. 표준출력 추가쓰기	: 1>>, >> ( 1 은 생략가능)
```
  cat 1>> a
  test
  ctrl+c
```

<br>

### 3. 표준 입력 	:  < 
> 키보드에 입력할 내용을 파일로 대체
```
  sort  : 정렬 명령어
  
  cat > a
  3
  1
  2
  ctrl +c
  
  sort < a
  1
  2
  3 
```

<br>

### 4. 표준 입력 	:  <<
> 오른쪽 입력값이 나올때까지 입력값을 받는다
```
  sort << a
  >4
  >2
  >1
  >3
  1		
  2
  3
  4
```

<br>

### 5. 표준 출력 & 표준에러 (2>&1)
> 정보
```
  2	: 표준 에러
  >	: 표준 출력 리다이렉션
  &	: 파일디스크립터 변환
  1	: 표준 출력 
  
  /dev/null	: 기록 대상이 되는 모든 데이터를 버리는 장치파일(휴지통)
``` 

#### 실습
> 예제1)
```
  ls -l /f323  /f233f2  /23f2  > test
  
  ls: cannot access /f323: 그런 파일이나 디렉터리가 없습니다		- 표준에러(2)	
  ls: cannot access /f233f2: 그런 파일이나 디렉터리가 없습니다	- 표준에러(2)
  ls: cannot access /23f2: 그런 파일이나 디렉터리가 없습니다		- 표준에러(2)
```

> 예제2)
```
  ls -l /f323  /f233f2  /23f2  > test 2>&1
```

> 예제3)
```
  ls -l /f323  /f233f2  /23f2 의 표준 출력(1)을 표준에러(2) 로 변환(2>&1)뒤 test 파일에 저장
  cat test
  ls: cannot access /f323: 그런 파일이나 디렉터리가 없습니다		- 표준에러(2)	
  ls: cannot access /f233f2: 그런 파일이나 디렉터리가 없습니다	- 표준에러(2)
  ls: cannot access /23f2: 그런 파일이나 디렉터리가 없습니다		- 표준에러(2)
```

> 예제4)
```
  ls -l /f323  /f233f2  /23f2  > /dev/null 2>&1
  -> 표준에러(2) 를 표준출력(1) 로 변환뒤에 /dev/null 로 보냄
```

<br>

파이프 라인(|) 
---
> 한명령어의 표준출력을 다른 명령어의 표준 입력으로 보내는 기능<br>왼쪽 명령의 결과를 받아서 오른쪽 명령어 적용


#### 실습
```
  ls -al /dev 
  
  ls -al /dev | cat -n
  
  ls -al /dev | cat -n | more
```

<br>

### [참고]  ; 
> 한번에 여러 명령어 실행
> 각 명령어를 독립적으로 수행


#### 실습
```
  mkdir /test100 ;touch /test100/a; ls -al /test100  
  
  ls -al /dev ; cat -n		--	x, 각 명령어 따로 실행
  
  ls -al /dev ; cat -n ; more 	--	x, 각 명령어 따로 실행
```

<br>

정리문제
---
```
  1. /etc/passwd 의 위에서 5번째 줄까지 출력
  
  2. inittab 파일 검색 후 별도로 아래서부터 12번째 줄까지 출력(find로 찾을것)
  
  3. /etc/ssh/sshd_config 문서를 20줄씩 끊어서 출력
  
  4. /etc/ssh/sshd_config 를 왼쪽에 번호표가 붙은 상태로 10줄씩 끊어서 출력
  
  5. /etc 디렉토리의 목록을 2줄씩 끊어서 출력하세요
  
  6. /etc 디렉토리의 목록을 왼쪽에 번호표가 붙은 상태로 출력하세요
  
  7. /cattest 디렉토리를 생성한 뒤 /cattest로 이동하세요(이후 문제는 이동하지말고 작업할 것)
  
  8. 가로로 1 2 3 내용을 가지는 파일 a , 세로로 1 2 내용을 가지는 파일 b를 생성하세요
  
  9. 파일 a 와 b 의 내용을 병합한 파일 c 를 생성하세요
  
  10. heath 내용을 가지는 파일 d 를 생성한 뒤 파일 c 의 내용을 d 파일에 추가시키세요
  
  11. /etc 왼쪽에 번호표를 가지면서 디렉토리의 목록의 내용을 가지는 파일 e 를 생성하세요
  
  12. grub.cfg login.defs  inittab 파일을 검색하여 /cattest 로 복사하고
      grub.cfg, login.defs, inittab, b, c, d, e 파일들의 위에서 2줄씩의 내용이 출력되는
      파일 f를 /home/test/c/d/cattest/linux 디렉토리에 생성하세요
```

<br>
