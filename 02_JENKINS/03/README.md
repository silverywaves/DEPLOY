# JENKINS INIT

<details>
  <summary><h2>EC2 공통 설정</h2></summary>

EC2 생성 기본 설정
---
1. EC2 LINUX(프리티어) 생성
2. 탄력적 IP 연결
3. SSH 연결
4. 보안규칙 설정( 8080 or 9090 열기)

<br>


> 참고 : root 계정 전환(명령어에서 제일 앞 sudo 빼고 작성)
```
  sudo su
```

<br>

TIMEZONE설정
---
```
  sudo rm /etc/localtime
  sudo ln -s /usr/share/zoneinfo/Asia/Seoul /etc/localtime
```

<br>

SWAP 설정 
---
> 스왑 파일 생성하기
```
  sudo dd if=/dev/zero of=/swapfile bs=128M count=16
```

<br>

> 스왑 파일에 대한 일기 쓰기 권한 업데이트하기
```
  sudo chmod 600 /swapfile
```

<br>

> Linux 스왑 영역 설정하기
```
  sudo mkswap /swapfile
```

<br>

> 스왑 공간에 스왑 파일을 추가하여 스왑 파일을 즉시 사용할 수 있도록 하기
```
  sudo swapon /swapfile
```

<br>

> 절차가 성공했는지 확인하기
```
  sudo swapon -s
```

<br>

> /etc/fstab 파일을 편집하여 부팅 시 스왑 파일을 활성화하기
```
  파일 열기
  sudo vi /etc/fstab
  
  파일 가장 마지막에 다음을 추가하고 :wq로 저장하고 종료
  /swapfile swap swap defaults 0 0
```

<br>

> free 명령어로 메모리 확인하기
```
  free
```

|-|
|-|
|![스크린샷 2024-06-14 095215](https://github.com/silverywaves/DEPLOY/assets/155939946/232e8a4b-353e-4352-8ba2-653ba2943846)|


</details>

<br>

<details>
  <summary><h2>EC2 기본 설정</h2></summary>


</details>



<br>

<details>
  <summary><h2>MySQL</h2></summary>

[mySQL](https://dev.mysql.com/downloads/)
---
|-|
|-|
|-|

</details>

