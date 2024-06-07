# VMware 로 리눅스 다루기
VMware 설치
---
### 1. [Download](https://softwareupdate.vmware.com/cds/vmw-desktop/ws/17.0.1/21139696/windows/core/) 
|-|
|-|
|![화면 캡처 2024-06-07 095339](https://github.com/silverywaves/LINUX/assets/155939946/00b10396-bcd2-48b4-abb2-3eaf2b57ec5d)|


<br>

### 2. 라이센스키 등록

<br>

CentOS Download
---
### 1. [Download](https://www.centos.org/download/)
|-|
|-|
|![화면 캡처 2024-06-07 095523](https://github.com/silverywaves/LINUX/assets/155939946/32f0d975-6e82-46ce-8d39-861c8493a0f4)|
|![화면 캡처 2024-06-07 095539](https://github.com/silverywaves/LINUX/assets/155939946/71101ca6-7bcb-44f4-b0d4-4bde9b7a4ae7)|
|![스크린샷 2024-06-07 100327](https://github.com/silverywaves/LINUX/assets/155939946/d8993518-0b7b-469d-a1dc-1a018dd3ba22)|


<br>

VMware Virtual Machine 생성
---
### 1. 가상머신 생성

|생성방법|
|-|
|![스크린샷 2024-06-07 095715](https://github.com/silverywaves/LINUX/assets/155939946/7b3ced4b-25e1-4fc5-b4fa-186878e8f7e9)|
|![스크린샷 2024-06-07 095729](https://github.com/silverywaves/LINUX/assets/155939946/c6dce03f-6dd1-47f6-ad03-d3336cfcfc4e)|
|![스크린샷 2024-06-07 095909](https://github.com/silverywaves/LINUX/assets/155939946/6fb02893-0271-44fd-bb61-3dadd29ecbba)|
|![스크린샷 2024-06-07 095916](https://github.com/silverywaves/LINUX/assets/155939946/3f931f09-d63a-49ca-85d4-c3eb49e40f81)|
|![스크린샷 2024-06-07 094057](https://github.com/silverywaves/LINUX/assets/155939946/65d115de-57a5-4372-974f-ff1419876f1d)|
|![스크린샷 2024-06-07 094136](https://github.com/silverywaves/LINUX/assets/155939946/715c63ac-8579-4b9c-a9f7-35f22d3b39d7)|
|![스크린샷 2024-06-07 094253](https://github.com/silverywaves/LINUX/assets/155939946/f1d0ed53-5f26-4b53-acb5-846972a0401b)|
|![스크린샷 2024-06-07 094304](https://github.com/silverywaves/LINUX/assets/155939946/9cf92059-ece8-4788-9a9a-56adba13efca)|
|![스크린샷 2024-06-07 094937](https://github.com/silverywaves/LINUX/assets/155939946/484f5893-bb34-47a8-8318-a22e1a66369a)|
|![스크린샷 2024-06-07 094946](https://github.com/silverywaves/LINUX/assets/155939946/3851be82-fd1a-496f-b2f4-fa99c417b95d)|
|![스크린샷 2024-06-07 094956](https://github.com/silverywaves/LINUX/assets/155939946/44e2b31d-a1ed-4ff8-811a-7d176368d96f)|
|![스크린샷 2024-06-07 095004](https://github.com/silverywaves/LINUX/assets/155939946/27883ead-f61b-4f94-a83e-7a06ec5217f2)|
|![스크린샷 2024-06-07 095021](https://github.com/silverywaves/LINUX/assets/155939946/d6800147-48f6-41af-899e-b9d4d6f15564)|
|![스크린샷 2024-06-07 095037](https://github.com/silverywaves/LINUX/assets/155939946/1ffdd82f-bf65-461e-89d5-7a4351ebd5c2)|
|![스크린샷 2024-06-07 095044](https://github.com/silverywaves/LINUX/assets/155939946/cbccbb52-0d6d-43f4-a0d7-c4ff1f452e89)|
|![스크린샷 2024-06-07 095058](https://github.com/silverywaves/LINUX/assets/155939946/ff0c49de-634a-41a7-a1b2-bc669724ea58)|

<br>

> Network Type
```
  Bridge : 호스트pc 그대로 사용
    외부 -통신-> 내부 : 가능
    내부 -통신-> 외부 : 가능
  
  Nat : 중간(VMWARE)에 nat라는 장치가 있어서 거기에 연결됨 : 보안통신 목적으로 사용
    내부 -통신-> 외부 : 가능
    외부 -통신-> 내부 : 불가능 
  
  HostOnly : 가상머신들(GuestPC)끼리만 통신 가능
    내부 -통신-> 외부 : 불가능
    외부 -통신-> 내부 : 불가능 
    GuestPC -통신-> GusetPC : 가능
```

<br>

### 2. 가상머신 설정

|안쓰는 장치 제거|
|-|
|![스크린샷 2024-06-07 100601](https://github.com/silverywaves/LINUX/assets/155939946/ab6a87f2-c6d9-4c07-bfe8-632fcb1de9c3)|
|![스크린샷 2024-06-07 100611](https://github.com/silverywaves/LINUX/assets/155939946/b410c0f7-8b48-4a86-aa2b-480c6fc3ca0b)|
|![스크린샷 2024-06-07 100618](https://github.com/silverywaves/LINUX/assets/155939946/60157eec-8ae6-4b2a-b7d2-97b70d716466)|
|![스크린샷 2024-06-07 100624](https://github.com/silverywaves/LINUX/assets/155939946/45ce68ed-187a-47d8-a198-fcdba692d91b)|
|![스크린샷 2024-06-07 100648](https://github.com/silverywaves/LINUX/assets/155939946/4548ea66-6d6a-4aff-a0dc-413caa68f605)|

<br>

### 3. 가산머신에 CentOS 연결

|Edit Virtual Machine settings|
|-|
|![스크린샷 2024-06-07 100738](https://github.com/silverywaves/LINUX/assets/155939946/e7620adb-0b6b-4b63-8d8e-6d113452a46d)|
|![스크린샷 2024-06-07 100754](https://github.com/silverywaves/LINUX/assets/155939946/afe9525a-f46a-4434-b80c-e7dd88674583)|
|![스크린샷 2024-06-07 100800](https://github.com/silverywaves/LINUX/assets/155939946/0853f493-7ab4-45eb-9c60-f4493a55bb3e)|
|![스크린샷 2024-06-07 100808](https://github.com/silverywaves/LINUX/assets/155939946/31775264-f8b9-4b35-a8af-c59c939b6eac)|

<br>

### 4. CentOS 설치
|-|
|-|
|![스크린샷 2024-06-07 101706](https://github.com/silverywaves/LINUX/assets/155939946/a0a63b29-8113-4fa4-a0e3-88c6d0625ee3)|
|![스크린샷 2024-06-07 101855](https://github.com/silverywaves/LINUX/assets/155939946/592133de-a301-4780-bd89-b79a537bc9e0)|
|![스크린샷 2024-06-07 101932](https://github.com/silverywaves/LINUX/assets/155939946/6e864782-5835-4b12-b99f-847d2b7b3571)|
|![스크린샷 2024-06-07 102010](https://github.com/silverywaves/LINUX/assets/155939946/e628ac7e-8333-4d12-8219-3cf6bce7f7c2)|

<br>

### 5. 사용자 생성 완료 후 접속해보기
|-|
|-|
|![스크린샷 2024-06-07 103805](https://github.com/silverywaves/LINUX/assets/155939946/d2d520c4-85b0-4db0-baf6-dd73d3c3c14d)
|![스크린샷 2024-06-07 103931](https://github.com/silverywaves/LINUX/assets/155939946/94724d53-0e30-4ba5-b3b9-c27a7d9cdffb)
|![스크린샷 2024-06-07 104102](https://github.com/silverywaves/LINUX/assets/155939946/ce8fae3d-e8d1-4a27-b8fb-8689a2ae29f0)|

<br>

### 6. 가상머신 네트워크 셋팅
|Edit → Virtual Network Editor|
|-|
|Change Settings|
|![스크린샷 2024-06-07 104215](https://github.com/silverywaves/LINUX/assets/155939946/20b36593-ad3d-45c1-8153-72e9613a3837)|
|![스크린샷 2024-06-07 104236](https://github.com/silverywaves/LINUX/assets/155939946/0c7bff29-0088-4af8-8cdb-c7e814a7ed81)|
|![스크린샷 2024-06-07 104513](https://github.com/silverywaves/LINUX/assets/155939946/965d3cb7-c405-4e3b-9683-c7ae264ad7f1)|
|![스크린샷 2024-06-07 104522](https://github.com/silverywaves/LINUX/assets/155939946/b021371d-075e-486d-9911-2f54c6f7bd8c)|
|![스크린샷 2024-06-07 105105](https://github.com/silverywaves/LINUX/assets/155939946/9be74907-bcb3-49f3-aff5-45659416dfc8)|
|접속확인해보기|
|![스크린샷 2024-06-07 105036](https://github.com/silverywaves/LINUX/assets/155939946/5d53301b-3722-45d9-aca3-a30772c8d488)|
|![스크린샷 2024-06-07 105135](https://github.com/silverywaves/LINUX/assets/155939946/c058641e-eb6f-42f7-8229-ee5e8436e4a8)|


<br>

> DNS

|-|
|-|
|![스크린샷 2024-06-07 105758](https://github.com/silverywaves/LINUX/assets/155939946/46122b6e-0eaa-44bd-b60f-d0070559e75a)|


<br>

### 7. 복구(Snapshot)
|-|
|-|
|LINUX_SERVER 탭 우클릭 → Snapshot → Take Snapshot|
|![스크린샷 2024-06-07 110724](https://github.com/silverywaves/LINUX/assets/155939946/9a32c318-2aa2-40b4-b823-1269192c5a8c)|
|문제 발생시 스냅샷 선택하면 해당 시점으로 돌아감|

<br>

원격통신툴 PuTTY
---
### 1. [PuTTY](https://www.putty.org/) 설치
> 서브컴퓨터 작동 전제

|-|
|-|
|![스크린샷 2024-06-07 111248](https://github.com/silverywaves/LINUX/assets/155939946/2f35e8be-75f1-4514-9881-79d6ab72fa94)|
|![스크린샷 2024-06-07 111314](https://github.com/silverywaves/LINUX/assets/155939946/8e9e659e-118b-4565-a7a2-78ed55d1d406)|


<br>

### 2. 셋팅 및 실행
|-|
|-|
|![스크린샷 2024-06-07 111712](https://github.com/silverywaves/LINUX/assets/155939946/dfbed0bd-d936-4b10-a3dd-192b11fbed0d)|
|![스크린샷 2024-06-07 111745](https://github.com/silverywaves/LINUX/assets/155939946/84e73c2f-cc7e-4f5b-8877-4c4721ee0d1f)|
|![스크린샷 2024-06-07 111805](https://github.com/silverywaves/LINUX/assets/155939946/f7dedf50-76bc-4e7b-aef8-a7d7e0006b4b)|
|![스크린샷 2024-06-07 111901](https://github.com/silverywaves/LINUX/assets/155939946/f3a4fc1d-10f6-4339-8867-a6773e94504c)|

<br>

> 화면 변경

|-|
|-|
|![스크린샷 2024-06-07 112006](https://github.com/silverywaves/LINUX/assets/155939946/a90e06a2-72c0-413b-9384-529488c4f415)|
|![스크린샷 2024-06-07 112104](https://github.com/silverywaves/LINUX/assets/155939946/6bcfddbe-7c62-47eb-8d0c-2100fe0b3b4c)|



