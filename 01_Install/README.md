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





