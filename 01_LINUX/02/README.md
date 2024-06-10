# 기본 명령어
참고사항
---
```
  윈도우는 대소문자 구분X
  리눅스는 대소문자 구분o
  ⇒ 경로 설정시 주의

  VMwara 바탕화면 우클릭 → 터미널 열기 : 윈도우 cmd 창과 유사함
```

<br>

01
---
> 패스워드 변경
```
  Passwd : 접속중인 사용자 패스워드 변경	(비밀번호 최소 6자리 root는 예외)
  Passwd [계정명] 해당 계정 pw 변경
```
<details>
<summary>실습</summary>

```
  [root@localhost ~]# passwd
  root 사용자의 비밀 번호 변경 중
  새  암호:
  잘못된 암호: 암호는 8 개의 문자 보다 짧습니다
  새  암호 재입력:
  passwd: 모든 인증 토큰이 성공적으로 업데이트 되었습니다.
  [root@localhost ~]# passwd user1
  user1 사용자의 비밀 번호 변경 중
  새  암호:
  잘못된 암호: 암호는 8 개의 문자 보다 짧습니다
  새  암호 재입력:
  passwd: 모든 인증 토큰이 성공적으로 업데이트 되었습니다.
```

</details>

<br>

> 재부팅
```
  reboot				
  shutdown -r now		
  init 6
```

<details>
<summary>실습</summary>

```

```

</details>

<br>

> 종료
```
  power off
  shutdown -h now
  Halt
  init 0
```

<details>
<summary>실습</summary>

```

```

</details>

<br>

> 참고 : RUN Level
```
  0  -  종료
  1
  2
  3
  4
  5  -  복원
  6  -  재부팅
```

02
---
> 네트워크 확인 명령어 = 인터페이스Config (IP 정보 확인시 사용)
```
  ifconfig
```

<details>
<summary>실습</summary>

```
  [root@localhost ~]# ifconfig
  ens32: ...
  
  lo: ...
  
  virbr0: ...
```

</details>

<br>

> 현재 위치 확인 명령어(Print Working Directory)
```
  pwd
```

<details>
<summary>실습</summary>

```
[root@localhost ~]# pwd
/root
```

</details>

<br>

> 디렉토리 변경 명령어 = 작업 경로 이동(Change Directory)
>> 절대 경로 : /(최상위 디렉토리) 가 기준 ⇒ / (최상위경로)를 기준 모든 하위경로를 포함
```
  cd [절대경로]  절대경로로 이동
```

>> 상대경로 : 현재 작업중인 디렉토리가 기준 ⇒ .(현재위치)를 기준으로 Low Level / High Level 이동
``` 
  cd user1 	현재 위치(/home)에서 하위디렉토리 user1 이동 (/home/user1)
  
  cd .		현재 디렉토리 (/home/user1)
  
  cd .. 	상위 디렉토리 이동 (/home)
  
  cd ..		상위 디렉토리 이동 (/)
  
  cd etc	현재 위치에서(/)에서 하위 디렉토리 etc 이동(/etc)
  
  cd ~		현재 접속중인 사용자의 홈디렉토리로 이동
```

>> 경로이동에 사용되는 특수문자
```
  .  : 현재 디렉토리
  .. : 상위 디렉토리
  ~(틸트) : 사용자의 홈디렉토리 
```

<details>
<summary>실습</summary>

> 절대경로
```
  [root@localhost ~]# cd /
  [root@localhost /]# pwd
  /
  [root@localhost /]# cd /home/user1
  [root@localhost user1]# pwd
  /home/user1
```

> 상대경로
```
  [root@localhost boot]# cd /home
  [root@localhost home]# pwd
  /home
  [root@localhost home]# cd ../dev	 => . 현재위치, .. 상위폴더, / 이동
  [root@localhost dev]# pwd
  /dev
  
  [root@localhost boot]# cd /home
  [root@localhost home]# cd user1	=> ./user1 : ./ 생략가능
  [root@localhost user1]# pwd
  /home/user1
  
  [root@localhost user1]# cd /dev
  [root@localhost dev]# pwd
  /dev
  [root@localhost dev]# cd ../home/user1
  [root@localhost user1]# pwd
  /home/user1
```

> cd ~
```
  [root@localhost user1]# cd ~
  [root@localhost ~]# pwd
  /root
```

</details>

<br>

> 문제1
```
  [환경]
  mkdir -p  /test/a/b/c/ /test1/f/g/h/
  
  
  1. cd 명령어를 절대경로(/가 기준) 을 이용해서 이동하세요
  
  1) /test/a 이동
  
  2) /test1/f/g 이동
  
  3) /test/a/b/c/ 이동
  
  4) /test1/f/g/h 이동
  
  2. cd 명령어를 상대경로(현재 위치가 기준) 을 이용해서 이동하세요
  
  현재위치를 cd /test/a로 이동
  
  1) /test/a/b/c/로 이동
  
  2) /test 로 이동
  
  3) /test1/f 로 이동
  
  4) /test1/f/g/h 로 이동
```

<details>
<summary>답</summary>

```

```

</details>

<br>

> 파일&디렉토리 목록 출력
```
  ls [옵션] [경로]
  
  -a : 모두보기
  -l : 자세히 보기
  -R : 하위까지 보기
  -d : 디렉토리 보기
  
  [실습]
  
  ls /etc/
  ls -l /etc/		법칙 1 [명령어][옵션][타겟]
  ls -al /etc/	a : 숨겨진 파일 확인(점이 찍혀있으면 숨겨져있는 파일/폴더)	법칙 2	명령어의 옵션은 조합이 가능하다
  ls -Ral /etc/  R : 하위 파일들까지 모두 조회
  cd /etc
  ls -l			법칙 3 상대경로에서의 작업은 생략이 가능하다.
  ls -ld /etc 
```

> 목록 표시 형식
```
  -rw-r--r--.  1 user1 user1   18 11월 25  2021 .bash_logout
  파일종류+허가권 소유권 용량 생성날짜 파일명
  - : 일반문서 파일
  d : 디렉터리 파일
```

<br>

> 디렉토리 생성 명령어(Make Directory)
```
  mkdir [옵션]

  -p : 상위디렉토리 포함 생성
  
  [실습]
  Mkdir /home/test
  
  Ls -l /home
  
  Mkdir /home/heath/a/b 	(x)
  Mkdir /home/heath/a 
  Mkdir /home/heath/a/b
  
  Ls -al /home/heath/a
  Mkdir  /home/test/c/d	(x)
  Mkdir -p /home/test/c/d/
```

> 명령어 정보 확인(manual)
```
  man
```

<br>

> 파일생성, 파일의 시간을 변경
```
  touch 파일명
  touch [옵션] [변경내용]
  
  -d 00:00 : (date time) 시간 
  -t YYYYMMDDHHmmss	 : 날짜시간 변경
  
  [환경]
  mkdir /touch
  cd /touch
  
  [실습]
  
  touch /touch/1	
  touch 2			 
  		
  touch /touch/3 4 ./5	 법칙 4 띄어쓰기시 새로운 옵션 및 경로가 지정된다.	
  
  touch -d 12:12 1
  
  touch - t 201601010101 6	날짜시간 지정 빈파일 생성
  
  cf) stat(파일 상태확인명령어) 6 하면  해당 파일의 변경날짜 확인 
```

<br>

> 복사(copy)
```
  cp [옵션]

  -i 질의(물어보는것)
  -r 강제 복사
  -r 디렉토리 복사
  -p 보존복사
  
  
  [환경]
  mkdir /touch /cptest 
  cd /cptest
```

<details>
<summary>실습</summary>

```
  -------------------------------
  [실습] - 파일복사(원본이름유지)
  -------------------------------
  
  cp /touch/1 /cptest/1		-- 파일 복사
  cp /touch/2 /cptest/		-- 파일 복사(생략가능)
  cp /touch/2 ~user1		-- 홈디렉토리로 복사
  
  -------------------------------
  [실습] - 파일복사(이름변경)
  -------------------------------
  cp /touch/3 /cptest/sam	
  cp /touch/4 /cptest/sa	
  
  -------------------------------
  [실습] - 파일복사(보존복사)
  -------------------------------
  cp -p /touch/3 /cptest/3
  cp -p /touch/4 /cptest/4
  cp -p /touch/2  /cptest/test	-- 이름 변경 보존복사
  
  -------------------------------
  [실습] - 디렉토리 복사
  -------------------------------
  
  cp -r /touch 	/cptest
  
  -------------------------------
  [실습] - 질의/강제 옵션
  -------------------------------
  
  cp -i /touch/1	/cptest	- 덮어쓰기여부 질의
  cp -f /touch/2  /cptest - 강제 덮어쓰기
  
  -------------------------------
  [실습] - 복수파일 복사
  -------------------------------
  
  cp -f /touch/1 2 ./3 /cptest/		법칙 5  여러 경로가 존재할 때 가장 마지막 경로가 타깃이 된다.
  
  
  ***cp 사용시 주의할 점
  
  원본과 타깃의 이름이 같은경우 file/dir 명 생략가능
  원본과 타깃의 이름이 다른 경우 	복사와 동시에 타깃 이름 변경
```

</details>

<br>

> 문제1
```
  1. /final 이라는 디렉토리 생성
    
  2. /final 디렉토리에 12, 34, 56 이라는 파일생성
  
  3. 34파일의 시간을 1999년 01월 01일 12:00 으로 변경
  
  4. /back 이라는 디렉토리 생성
  
  5. /final 의 12 ,56 파일을 /back  디렉토리에 복사
  
  6. /final 의 34 파일을 /back 디렉토리에 보존복사
```

<details>
<summary>답</summary>
  
```
  [root@localhost /]# mkdir final
  [root@localhost /]# cd final
  [root@localhost final]# pwd
  /final
  [root@localhost final]# touch 12
  [root@localhost final]# touch 34
  [root@localhost final]# touch 56
  [root@localhost final]# touch -t 199901011200 34
  [root@localhost final]# stat 34
    File: `34'
    Size: 0               Blocks: 0          IO Block: 4096   일반 빈 파일
  Device: fd00h/64768d    Inode: 67367779    Links: 1
  Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
  Context: unconfined_u:object_r:default_t:s0
  Access: 1999-01-01 12:00:00.000000000 +0900
  Modify: 1999-01-01 12:00:00.000000000 +0900
  Change: 2024-06-10 10:38:00.916994120 +0900
   Birth: -
  [root@localhost final]# ls -l
  합계 0
  -rw-r--r--. 1 root root 0  6월 10 10:37 12
  -rw-r--r--. 1 root root 0  1월  1  1999 34
  -rw-r--r--. 1 root root 0  6월 10 10:37 56
  [root@localhost bank]# mkdir /back
  [root@localhost bank]# cd /back
  [root@localhost back]# pwd
  /back
  [root@localhost back]# cp /final/12 /final/56 /back/
  [root@localhost back]# cp -p /final/34 /back/
```
</details>

<br>
