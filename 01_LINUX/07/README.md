# 계정
/etc/login.defs : 보안관련 설정(모든계정적용)
---
```
  MAIL_DIR        /var/spool/mail
  
  PASS_MAX_DAYS   99999		패스워드 최대 사용일
  PASS_MIN_DAYS   0		패스워드 최소 사용일		
  PASS_MIN_LEN    5			패스워드 최소 길이
  PASS_WARN_AGE   7		패스워드 만료 경고일
  
  UID_MIN                   500		UID의 최소 최대 범위
  UID_MAX                 60000
  
  GID_MIN                   500		GID의 최소 최대 범위
  GID_MAX                 60000
  
  CREATE_HOME     yes		홈디렉토리 생성여부
  
  UMASK           077			홈디렉토리의 Umask 값
  USERGROUPS_ENAB yes		사용자 계정 삭제시 그룹 삭제 여부 
  
  ENCRYPT_METHOD SHA512		암호화 기법
  
  CentOS 5.2 = MD5
  CentOS 6.2 = SHA512
```

<br>

/etc/default/useradd : 계정 기본 경로 설정 (모든계정적용)
---
```
  GROUP=100	그룹지정(100 :UID 와 동일한 GID명)
  HOME=/home	홈디렉토리 위치
  INACTIVE=-1	패스워드 만료후 계정 사용 불가능 되는 날 지정(-1 :사용안함, 0:기간없음[계정정지],1 : 하루,,,,)
  EXPIRE=		계정의 패스워드 만료일(비어있으면 무제한)
  SHELL=/bin/bash	로그인시 사용되는 쉘 경로
  SKEL=/etc/skel	스컬디렉토리 경로
  CREATE_MAIL_SPOOL=yes	메일함 생성여부
```

### 주의
```
  메일함 생성여부 : /etc/default/useradd 
  메일함 디렉토리설정 : /etc/login.defs
  계정 생성여부 : /etc/login.defs
  계정 홈위치 :	/etc/default/useradd
```

<br>

생성한 계정 정보 저장
---
### 1. /etc/passwd (계정 기본정보저장) 	
```
  1)      2)3)   4)  5)  6)               7)
  heath:x:503:503:  :/home/heath:/bin/bash
  
  1) 계정명
  2) 패스워드(x-> /etc/shadow에 저장)
  3) UID(계정구별)
  4) GID(그룹)
  5) Comment(주석)
  6) 홈디렉토리 경로(작업위치)
  7) 사용하는 쉘 경로
```

<br>

### 2. /etc/shadow (계정 패스워드 정보저장)
```
  1)      2)  3)  4)5)    6)   7) 8)
  heath:!!/:17216:0:99999:7  :  :  :
  
  1)계정명
  2)암호화된 패스워드 저장공간
  3)패스워드 생성날짜(1970.01.01이후)
  4)패스워드 최소사용날짜
  5)패스워드 최대사용날짜
  6)패스워드 만료 경고일 
  7)만료시 비활성화 옵션(-1:미설정, 0:바로만료,1:하루연장)
  8)만료지정일 
```

> 패스워드 설정시 !! 부분의 암호화된 패스워드 저장
```
  heath:$6$gAQ20msY$lRejdUefR4ytjO2CjhzcJCX5EQYPk3c.3HpOtyqpCye4C6fo5MbaLZPOwajWhielmTlxUf8dls11.KiGHp5e1/:17216:0:99999:7:::
```

<br>

### 3. /etc/group (그룹계정 정보 저장)
```
  heath:x:503:
```

<br>

### 4. /home/계정명(사용자의 홈디렉토리 생성 & 기본프로필 환경저장)
```
  .bash_profile	: 로그인쉘 프로필파일	
  .bashrc		: 서브쉘 프로필파일
  .bash_logout	: 로그아웃시 적용할 설정
  .bash_history	: 명령 기록 보존 파일
```

<br>

### 5./var/spool/mail/계정명(사용자 계정의 임시 메일함 생성)

<br>


useradd : 사용자 계정 생성명령어
--- 
### 옵션
```
  -u :UID 지정
  -g :주그룹 지정
  -G :보조 그룹 지정
  -c : 주석,설명
  -d : 홈디렉토리 경로 지정
  -m:  메뉴얼 참조(man useradd)
  -k : 스컬디렉토리 경로 지정
  -s : 쉘 지정 
```

<br>

### 실습 -옵션 적용
> 유저 생성1
```
  useradd test1
  useradd -u 510 test2	
```

<br>

> 유저 생성2(그룹지정)
```
  useradd -g test1 test3	
  cf) 그룹을 지정하지 않으면 uid와 동일한 gid의 그룹이 생성된다
  useradd -G heath test4		
```

<br>

> 유저 생성3(주석,설명)
```
  useradd -c itbank test5
```

<br>

> 유저 생성4(홈디렉토리경로지정)
```
  useradd -d /export/home/test6 test6
  useradd -d /export/home test8
  useradd -d /export/home/heath test9
  주의1 ) 홈디렉토리 경로 변경시 해당되는 홈디렉토리를 먼저 생성해야 한다.
  주의2 ) 홈디렉토리 경로 지정시 경로 끝에 계정명과 동일한 홈디렉토리명까지 기재할 것
```

<br>

> 유저 생성5(스컬 경로 지정)
```
  useradd -m -k /skeltest test7
  cf)skel 디렉토리 홈디렉토리를 구성하는 뼈대, 계정 생성시 한번만 복사한다.
```

<br>

> 유저 생성6(쉘 지정)
```
  useradd -s /bin/ksh test10	=> -s 쉘지정
```

<Br>

#### 미니 문제
```
  1. test10 계정 생성시 UID 값 1800 으로 지정
  2. test20 계정 생성시 주그룹을 test10 으로 지정
  3. test30 계정 생성시 보조그룹 test10 추가
  4. test40 계정 생성시 홈디렉토리 경로를 /export/test40 으로 지정
  5. test50 계정 생성시 스컬경로를 /skel2 로하고 test50홈디렉토리에 test50파일
  이 생성되도록 하세요
  6. test60 계정 생성시 쉘을 /bin/ksh 로 설정 
```

<details>
  <summary>답</summary>
  
```
  
```

</details>

<br>

usermod : 사용자 계정정보 변경 명령어
---
### 옵션
```
-d 홈디렉토리 설정 	
-m 홈디렉토리 이동
```

<br>

### 실습
```
usermod -u 2000 mod  	-u uid 변경
usermod -g heath mod	-g 주그룹 변경
usermod -G test1 mod	-G 보조그룹 변경
usermod -c linux mod	-c 계정 설정변경
usermod -s /bin/sh mod	-s 쉘변경
mkdir -p /export/home
usermod -md /export/home/mod mod
``` 

<br>

#### 미니 문제(스냅샷 돌리고 문제풀기)
```
  useradd test1,test2,test3
  
  1. test1,test2,test3 계정 생성
  2. test1 의 comment 를 modtest로 변경
  3. test2 의 주그룹을 test1로, test2의 보조그룹을 test3으로 지정
  4. test1 의 shell을 /bin/ksh 로변경
  5. test1의 홈디렉토리를 /test1/home 경로로, test2 홈디렉토리를 /test2/home으로 이동
```

<details>
  <summary>답</summary>
  
```
  
```

</details>

<Br>

userdel: 계정 삭제 명령어
---
### 옵션
```
  -r
```

<br>

### 실습
```
  userdel mod 	-계정삭제
  
  		/etc/passwd		삭제
  		/etc/shadow		삭제
  		/etc/group 		삭제
  		/home/mod		존재
  		/var/spool/mail/mod	존재
  
  
  userdel -r itbank
  
  		/etc/passwd		삭제
  		/etc/shadow		삭제
  		/etc/group 		삭제
  		/home/mod		삭제
  		/var/spool/mail/mod	삭제
```

<br>

#### 연습문제
> 계정 생성 
```
  1.test1 계정 생성시 UID 를 4000으로 지정하세요 
  2.test2 계정 생성시 주그룹을 test1으로 지정하세요
  3.test3 계정 생성시 보조그룹을 test1으로 지정하세요
  4.test4 계정 생성시 기본쉘 경로를 /bin/ksh로 지정하세요
  5.test5 계정 생성시 스컬의 기본경로를 /skeltest로 지정하고
  홈디렉토리에 자동으로 Public_html디렉토리가 생성되도록 하세요
```

<details>
  <summary>답</summary>
  
```
  
```

</details>

<br>

> 계정 수정
```
  1.test1 계정의 UID를 5555로 변경하세요
  2.test2 계정의 주그룹을 test3으로 변경하세요
  3.test3 계정의 보조그룹 test1 추가하세요
  4.test4 계정의 홈디렉토리를 /export/home/test4로 변경하세요
  5.test5 계정의 쉘경로를 /bin/sh로 변경하세요
```

<details>
  <summary>답</summary>
  
```
  
```

</details>

<br>

> 계정 삭제
```
  1.test4 계정을 삭제 하고 삭제되지 않는 파일이나 디렉토리는 
  rm 명령어로 삭제하세요
  2.test5 계정을 작업내용 포함 삭제하세요
```

<details>
  <summary>답</summary>
  
```
  
```

</details>

<br>

그룹 계정 관련 명령어
---
```
  groupadd		: 그룹 계정 생성 명령어
  groupmod	: 그룹 계정 변경 명령어	
  groupdel		: 그룹 계정 삭제 명령어
```

### 옵션
```
  -g :GID 설정
```

<Br>

### 실습
```
  groupadd g1
  groupadd -g 700 g2
  groupadd g3
  groupmod -g 699 g1
  groupdel g3
  groupadd g1
```

<br>

> cf
```
  계정이나 그룹을 생성하면 바로 이전에 생성했던 uid/gid의 다음번으로 생성된다.
```

<br>

/etc/default/useradd
---
### 1) vi /etc/default/useradd로 변경
```

```

<br>

### 2) useradd -D 명령어로 변경
```

```

<br>

### 옵션
```
  -s : 기본쉘변경
  -b : 기본 홈디렉토리 변경
```

<br>

### 실습
```
  useradd -D -s /bin/ksh
  
  useradd test200
  cat /etc/passwd
  
  useradd -D -b /export/home 
  
  useradd test201
  cat /etc/passwd
```
> /etc/default/useradd 를 다시 원래설정으로 변경

<br>

#### 미니문제
```
  userdel -r test1
  userdel -r test2
  userdel -r test3
```

<details>
  <summary>답</summary>
  
```
  
```

</details>

<br>

> 1.
```
  명령어를 이용해서 홈디렉토리의 기본경로를 /export/hometest 로 변경하고
  test1 계정을 만드세요
```

<details>
  <summary>답</summary>
  
```
  
```

</details>

<br>

> 2
```
  명령어를 이용해서 쉘의 기본경로를 /bin/sh로 변경하고
  test2 계정을 만드세요
```

<details>
  <summary>답</summary>
  
```
  
```

</details>

<Br>

> 3. 
```
  vi를 이용해서 쉘의 기본경로를 /bin/bash, 홈디렉토리 경로를 /home으로 되돌리고
  test3 계정을 만드세요
```

<details>
  <summary>답</summary>
  
```
  
```

</details>

<Br>

명령어 없이 계정 생성
---
```
  1. /etc/passwd
  vi /etc/passwd -> 맨마지막줄이동 한행 복사후 수정
  
  2. /etc/group
  vi /etc/group -> 맨마지막줄이동, 한행 복사후 수정
  
  3. 스컬경로 복사
  cp -r /etc/skel /home/생성계정명
  chmod 700 ~생성계정명
  chown 생성계정명.생성계정명 ~생성계정명
  
  4. 메일함 생성
  cd /var/spool/mail
  touch 생성계정명
  chmod 660 생성계정명
  chown 생성계정명.생성계정명 생성계정명
  
  5. 패스워드 설정
  passwd 생성 계정명
  
  6. 로그인 해보기
```

<br>

#### 미니 문제
> 1. useradd 명령어 없이 test1010 만드세요

<details>
  <summary>답</summary>
  
```
  
```

</details>

<br>

> 2. useradd 명령어 없이 test2020 만드세요 

<details>
  <summary>답</summary>
  
```
  
```

</details>

<br>

chage
---
> 사용자의 암호 주기 변경 설정

### 옵션
```
  -m	: 암호 최소 사용일자 지정
  -M	: 암호 최대 사용일자 지정
  -E	: 암호 만료일 지정
  -W	: 만료 경고일 지정
```

<br>

### 실습
#### 암호 최소 사용일
> 적용
```
  chage -m 10 user0
  or
  passwd -n 10 user0
```

> 확인
```
  chage -l user0
```

<br>

#### 암호 최대 사용일
> 적용
```
  chage -M 90 user0
  or
  passwd -x 90 user0
```

> 확인
```
  chage -l user0
```

<Br>

#### 암호 만료 경고일
> 적용
```
  chage -W 5 user0
  or 
  passwd -w 5 user0
```

> 확인
```
  chage -l user0
```

<Br>

#### 계정 정지 만기일 설정
> 적용
```
  chage -I 10 user0
  or 
  passwd -i 10 user0
```

> 확인
```
  chage -l user0
```

<br>

#### 다음 로그인시 암호 강제 변경
> 적용
```
  passwd -e user0
```

<br>

특수문자
---
```
  ~ 	홈 디렉토리
  .	현재 디렉토리
  ..	상위디렉토리
  #	주석	
  $	쉘변수
  *	전체 문자 와일드 카드
  ?	한문자 와일드 카드
  []	문자의 범위지정
  ;	쉘명령 구분자
  |	파이프라인
  <	리다이렉션(표준입력)
  >	리다이렉션(표준출력-덮어쓰기)
  >>	리다이렉션(표준출력-추가하기)
  &&	and연산
  ||	or연산
```




