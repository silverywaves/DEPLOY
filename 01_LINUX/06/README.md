# 권한
권한
--
|-|
|-|
|![image](https://github.com/silverywaves/DEPLOY/assets/155939946/41fda749-de66-4588-aa9c-0fd4fc49f237)|

|구분|파일|디렉토리|
|:-:|-|-|
|r : 읽기|r : 문서 내용 보기<br>(cat,head,tail,more,vi)|r : 디렉토리 내 목록보기<br>(ls)|
|w : 쓰기|w : 문서 내용 편집<br>(vi, >)|w : 디렉토리 내 생성/수정/삭제<br>(mkdir,touch,cp,mv,rm..)|
|x : 실행|x : 실행파일<br>(./파일명)|x : 디렉토리 진입권한<br>(cd)|

<br>

#### 미니문제
```
rw_r_xr__	-> 654
rwxr__r_x	-> 745
r__rwxr__	-> 474
r_xr__r_x	-> 545
r__r_x___	-> 450

755	-> rwxr_xr_x
644	-> rw_r__r__
701	-> rwx_____x
542	-> r_xr___w_
643	-> rw_r___wx
375	-> _wxrwxr_x
```

<br>

허가권
---

> 실습
```
[root@localhost vitest]# mkdir /perm
[root@localhost vitest]# ls -ld /perm
drwxr-xr-x. 2 root root 6  6월 11 11:34 /perm
[root@localhost vitest]# chmod u-rw /perm
[root@localhost vitest]# ls -ld /perm
d--xr-xr-x. 2 root root 6  6월 11 11:34 /perm
[root@localhost vitest]# chmod u=rw /perm
[root@localhost vitest]# ls -ld /perm
drw-r-xr-x. 2 root root 6  6월 11 11:34 /perm
[root@localhost vitest]# chmod g=w /perm
[root@localhost vitest]# ls -ld /perm
drw--w-r-x. 2 root root 6  6월 11 11:34 /perm
[root@localhost vitest]# chmod o=w /perm
[root@localhost vitest]# ls -ld /perm
drw--w--w-. 2 root root 6  6월 11 11:34 /perm
[root@localhost vitest]# chmod u+x,g+r,o-w /perm
[root@localhost vitest]# ls -ld /perm
drwxrw----. 2 root root 6  6월 11 11:34 /perm
[root@localhost vitest]# chmod a=rx /perm
[root@localhost vitest]# ls -ld /perm
dr-xr-xr-x. 2 root root 6  6월 11 11:34 /perm
[root@localhost vitest]# chmod a= /perm
[root@localhost vitest]# ls -ld /perm
d---------. 2 root root 6  6월 11 11:34 /perm
[root@localhost vitest]# chmod 754 /perm
[root@localhost vitest]# ls -ld /perm
drwxr-xr--. 2 root root 6  6월 11 11:34 /perm
```

<br>

소유권
---

> 실습
```
[root@localhost vitest]# chown user1:user1 /perm
[root@localhost vitest]# ls -ld /perm
d--x-w--wx. 2 user1 user1 6  6월 11 11:34 /perm
[root@localhost vitest]# chown user2 /perm
[root@localhost vitest]# ls -ld /perm
d--x-w--wx. 2 user2 user1 6  6월 11 11:34 /perm
[root@localhost vitest]# chown :user3 /perm
[root@localhost vitest]# ls -ld /perm
d--x-w--wx. 2 user2 user3 6  6월 11 11:34 /perm
[root@localhost vitest]# chown root.root /perm
[root@localhost vitest]# ls -ld /perm
d--x-w--wx. 2 root root 6  6월 11 11:34 /perm
```

<br>

