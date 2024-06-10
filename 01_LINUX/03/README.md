# 기본명령어
04
---
> mv : 파일 디렉토리 이동(옵션x)
```
  [환경]
  mkdir /mvfile /mvtest
  cd /mvfile
  touch 1 2 3 4 
  mkdir a b c 
  cd /mvtest
  
  
  [실습]
  1. mv /mvfile/1 	/mvtest/1		
  2. mv /mvfile/2 	/mvtest			
  3. mv /mvfile/a 	./			
  4. mv /mvfile/3	/mvfile/b	/mvfile/c 	/mvtest	
  5. mv /mvfile/4	/mvtest/sa		
```

<br>

> rm :파일&디렉토리 삭제(remove)
```
  [옵션]
  -f : 강제 삭제
  -r : 디렉토리 삭제
  -i : 질의(y/n)
  
  [환경]
  mkdir /rmtest 
  cd /rmtest
  touch 1 2 3 4
  mkdir a b c 
  
  [실습] 
  
  rm 1
  rm a
  rm -r a
  rm -f 2
  rm -i 3 	
  rm -fi 3		법칙 6 모순되는 옵션 사용시 마지막 옵션 적용
  rm -if 3 	
  rm -rf b c
```

<br>

> find : 파일&디렉토리 검색
```
  [옵션]
  name  	: 파일/디렉토리명 검색
  perm 	: 지정된 퍼미션 검색 
  size 	: 파일 크기가 일치하는 파일 찾기 
  type	: 파일 형식 지정함
  exec 	: 검색 결과를 해당 명령어로 실행 하는 옵션
  
  o	: 복수 옵션 적용
  type 	: 파일 유형검색 (파일 or 디렉토리)
  
  atime n	: n일 전에 엑세스한 파일 찾기, +n 또는 -n 형식으로도 사용가능
  mtime n	: n일 전에 마지막으로 수정된 파일 찾기, +n 또는 -n 형식으로도 사용가능
  newer	: 지정된 파일 이후 생성된 파일 찾기 
  used n	: 변경된지 n일이 지난 모든 파일 찾기
  uid	: 지정된 UID를 가진 파일 검색
  gid	: 지정된 GID를 가진 파일 검색
  group	: 지정된 그룹을 가진 파일 검색
  user	: 지정된 소유자가 소유한 모든 파일 검색
  
  [환경]
  mkdir /test /exec /exec2 
  cd /test
  mkdir  aa ab ca dd eae
  touch 11 21 31 44 524 
  
  
  [실습 1]  문자검색
  find /test -name 11
  find /test -name aa
  find /test -name 21
  
  
  [실습 2]  포함 문자 검색
  find  /test -name "a*"
  find  /test -name "*a"
  find  /test -name "*a*"
  
  [실습 3]  파일 종류 검색
  find /test -type f
  find /test -type d
  find /etc -type l
  find /etc -type d
  
  [실습 4] - 다른 옵션 복수 적용
  find / -name user1
  find / -name user1  -type f
  find / -name user1  -type d
  
  [실습 5] - 같은 옵션 복수 적용
  find /test -type d
  find /test -type f
  find /test -type d -type f	(x)
  find /test -type d -o -type f	o
  find /test -name 1 -o -name 2 	
  
  [실습 6] -같은 옵션 복수 적용 예외(용량 검색)
  find / -size +30000k 
  find / -size -30000k
  find / -size +30000K -size -50000K 
   
  [실습 7] - 외부 명령어 실행(추가중)
  find /test -exec ls -l {} \;
  find /test -exec cp -r {} /exec \;
  find /test -type d -exec ls -l {} \;
  find / -name user1 -type d -exec cp -r {} /exec2 \;
```


> 문제
```
  1. 
  /findtest 디렉토리를 만들고 그안에 a,b,c,d 디렉토리, 1,2,3,4파일을 만든후 
  find 명령어를 이용해서 login.defs을 찾아 /findtest에 복사하세요(/etc/에 있는 파일복사)
  
  2.
  find 명령어를 이용해서 passwd,inittab 한줄명령어로 찾고
  /findtest 에 복사하세요(/etc/에 있는 파일복사)
  
  3. find 명령어를 통해 /findtest 안의 내용중 파일만 검색하세요
  	
  4.find 명령어를 통해 /findtest 의 모든 디렉토리의 목록을 볼 수있도록 한줄명령어로 해결하세요
```

<details>
  <summary>답</summary>

```

```
  
</details>

<br>

05
---
> alias : 별칭, (명령어)단축키
```
  [옵션]x
  
  [실습]-1
  alias a1='mkdir /aliastest'
  a1
  ls -al /aliastest
  
  [실습]-1 명령어 지정
  alias a2='touch /aliastest/a /aliastest/b'
  a2
  ls -al /aliastest
  
  [실습]-2 명령어 지정
  alias a3='touch /aliastest/test1
  	>mkdir /aliastest/test2'
  a3
  ls -al /aliastest
  
  [실습]-3 alias 조합 사용
  alias a4='a1
  	> a2'
  ls -al /aliasteset
  
  [실습]-4 ailas 삭제 
  unalias a1 a2 a3
```

<br>

> 문제
```
  /aliastest 디렉토리를 삭제후에 진행하세요 (rm -rf /aliastest )
  
  1./aliastest 디렉토리를 만드는 alias a1 을 생성하세요
  2. /aliastest 안에 빈파일 test1 test2 test3 을만드는 alias a2 를 생성하세요
  3. /aliastest 안의 빈파일 test1 test2 test3 의 시간을 11:30으로  으로 변경하는 alias a3 을 생성하세요
  4. find 명령어를 이용해서 login.defs, passwd, inittab 을 /aliastest 디렉토리로 복사시키는 alias a4를 생성하세요
  5. a1,a2,a3,a4 를 한번에 사용할 수 있는 alias a5 를 만드세요
  6. /aliastest 를 삭제하는 alias a6를 생성하세요
```

<details>
  <summary>답</summary>

```

```

</details>

<br>

06
---
> date : 시스템 시간 확인
```
  Date -s “2016-09-09 22:24:30”		- 날짜 시간 모두 설정
  Date +%D -s “2016-09-09”		- 날짜만 설정
  Date +%T -s “22:42:30”		- 시간만 설정
  Date ‘+%Y-%m-%d %H:%M:%S’		- 내가 원하는 방식으로 출력
```

<br>

> cal : 달력 보기
```
  cal [월][연]
  cal 2015
  cal 09 2016
```

<br>

> hwclock : 하드웨어 시간 
```
  Hwclock 		- 현재 하드웨어 시간확인
  Hwclock -w 		- 하드웨어 시간변경(시스템시간으로)
  Hwclock -s 		- 시스템 시간변경(하드웨어 시간으로)
```

<br>

> rdate 하드웨어-시스템 시간 동기화
```
  rdate time.bora.net
  rdate -s time.bora.net
```

<br>

07
---
> cat : 문서 전체 출력 <br>
```
  [옵션]
  -n  : 행번호 출력
  
  [실습]
  cat /etc/passwd
  cat -n /etc/passwd
```

<br>

> head&tail : 위&아래에서 시작해서(기본10줄) 출력<br>

```
  [옵션]
  -숫자 : 지정된 숫자 줄수만큼 출력
  
  [실습]
  
  head /etc/passwd
  head -5 /etc/passwd 	
  head -2 /etc/passwd 
  tail /etc/passwd
  tail -5 /etc/passwd
```

<br>

> more : 화면크기만큼 출력<br>
```
  more /etc/passwd
```

<br>

> 문제 <br>

```
  1. /output 디렉토리 만든 후 /etc/passwd, /etc/inittab, /etc/login.defs 를 복사
  2./output/login.defs 의 내용을 위에서부터 5줄만 확인하세요
  3./output/inittab 의 내용을 아래서부터 5줄만 확인하세요
  4./output/passwd의 내용을 화면 크기만큼 끊어서 확인하세요
  5. /output/passwd의 내용을 행번호를 붙여서 확인해보세요
  6. find 명령어를 이용해서 /output 디렉토리 안의 login.defs , inittab, passwd의 
  내용을 위로 5행만 출력하는 alias a1 을 만들고 실행해서 확인해 보세요
```

<details>
  <summary>답</summary>

```

```

</details>

<br>
