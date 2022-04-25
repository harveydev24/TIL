# OS

[Reference: 운영체제, 반효경(이화여대) ](http://www.kocw.or.kr/home/cview.do?mty=p&kemId=1046323)

---



# 1. Introduction to Operating System

## 운영 체제란?

- 컴퓨터 하드웨어 바로 위에 설치되어 사용자 및 다른 모든 소프트웨어와 하드웨어를 연결하는 소프트웨어 계층
- 좁은 의미의 운영 체제 (커널)
  - 운영 체제의 핵심 부분으로 메모리에 상주하는 부분
  - 일반적으로 OS를 의미
- 넓은 의미의 운영 체제
  - 커널 뿐 아니라 각종 주변 시스템 유틸리티를 포함한 개념
  - 메모리에 상주하지 않는 독립적인 프로그램들을 포함



## 운영 체제의 목적

- 컴퓨터 시스템의 자원을 효율적으로 관리
  - 프로세서, 기억장치, 입출력 장치 등의 리소스를 효율적으로 관리
    - 프로그램 간의 형평성 있는 자원 분배
    - 주어진 자원으로 최대한의 성능 발휘
- 컴퓨터 시스템을 편리하게 사용할 수 있는 환경 제공



## 운영 체제의 분류

### 동시 작업 가능 여부

- 단일 작업 (single tasking)
  - 한 번에 하나의 작업만 처리
  - MS-DOS 프롬프트 상에서는 한 명령의 수행을 끝내기 전에 다른 명령을 수행시킬 수 없음
- 다중 작업 (multi tasking)
  - 동시에 두 개 이상의 작업 처리
  - UNIX, MS Windows 등에서는 한 명령의 수행이 끝나기 전에 다른 명령이나 프로그램을 수행할 수 있음

### 사용자의 수

- 단일 사용자 (single user)
  - MS-DOS, MS Windows
- 다중 사용자 (multi user)
  - UNIX, NT server
  - 보안 기능 필요
  - 현재는 대부분의 운영 체제가 여기에 속함

### 처리 방식

- 일괄 처리 (batch processing)
  - 작업 요청을 일정량 모아서 한꺼번에 처리
  - 작업이 종료될 때까지 기다려야 함
  - 현대 운영 체제에서는 찾아보기 힘듦
- 시분할 (time sharing)
  - 여러 작업을 수행할 때 컴퓨터의 처리 능력을 일정한 시간 단위로 분할하여 사용
    - 짧은 시간동안 여러 프로그램에 리소스를 번갈아 할당
  - 일괄 처리 시스템에 비해 짧은 응답 시간을 가짐
  - interactive한 방식
  - 정확한 시간을 지켜주는 시스템은 아님
    - 사람의 사용성에 집중
  - 현대 운영 체제의 주된 방식
    - Linux, Windows, IOS, Android 등
- 실시간 (real time)
  - 정해진 시간 안에 어떠한 일이 반드시 종료됨이 보장되어야 하는 실시간 시스템을 위한 운영 체제
  - 원자로/공장/미사일/반도체 장비/로봇 제어 등 특수한 목적을 가짐
  - 실시간 시스템의 개념 확장
    - Hard realtime system
      - 데드라인을 못지키면 치명적 결과 초래
    - Soft realtime system
      - 데드라인을 못지키면 경미한 결과 초래



## 혼동하기 쉬운 용어들

- 컴퓨터에서 여러 작업을 동시에 수행하는 것
  - Multitasking
  - Multiprogramming
    - 여러 프로그램이 메모리에 올라가 있음을 강조
  - Time Sharing
    - CPU의 시간을 분할하여 나누어 쓴다는 점을 강조
  - Multiprocess

- Multiprocessor
  - 하나의 컴퓨터에 CPU (processor)가 여러개 붙어 있음을 의미



## 운영 체제의 예시

### UNIX

- 대형 컴퓨터를 위해 만들어진 운영 체제
- C언어로 작성
  - C언어는 UNIX를 위해 개발된 언어
    - 어셈블리어로 코딩하는 것이 어려웠기 때문에 개발됨
    - 사람하고 가까운 고급 언어이지만, 기계어하고도 가까움
- 높은 이식성
  - 다양한 컴퓨터에 설치할 수 있음
- 최소한의 커널 구조
  - 메모리에 상주하는 커널에는 핵심적인 요소만 들어가있음
- 복잡한 시스템에 맞게 확장 용이
- 초창기에 소스 코드 공개
  - 프로그램 개발에 용이
- 다양한 버전 존재
  - System V, FreeBSD, SunOS, Solaris
  - Linux
    - 오픈 소스
    - 개인용으로 쓰기에도 좋음

### Windows

- 개인용 컴퓨터를 위해 만들어진 다중 작업용 GUI 기반의 운영 체제
- DOS용 응용 프로그램과 호환성 제공
- 네트워크 환경 강화
- 풍부한 지원 소프트웨어



## 운영 체제의 전반적인 구조

- CPU
  - CPU 스케쥴링
- Memory
  - 메모리 관리
- Disk
  - 파일 관리
- I/O device
  - 입출력 관리
- 그 외
  - 프로세스 관리
  - 보호 시스템
  - 네트워킹
  - 명령어 해석기 (Command Line Interpreter)



<br>

<br>

# 2. System Structure & Program Execution

## 컴퓨터 시스템의 구조

![image-20220425204556935](README.assets/image-20220425204556935.png)

- Computer

  - CPU

    - 매 클락사이클 마다 메모리에서 기계어(instruction)를 읽어서 프로그램 실행
    - Register
      - 메모리보다 빠르면서 정보를 저장할 수 있는 작은 공간
    - Mode bit
      - 사용자 프로그램의 잘못된 수행으로 다른 프로그램 및 운영 체제에 피해가 가지 않도록 하기 위한 보호 장치
      - CPU를 통해 실행되고있는 것이 OS인지, 프로그램인지 구분
      - 하드웨어적으로 두 가지 모드의 operation 지원
        - 사용자 모드->1
          - 사용자 프로그램 수행
        - 모니터 모드 (=커널 모드, 시스템 모드)->0
          - OS 코드 수행
      - 보안을 해칠 수 있는 중요한 명령어는 모니터 모드에서만 수행 가능한 특권명령으로 규정
        - I/O 관련
      - Interrupt나 Exception 발생 시 하드웨어가 mode bit을 0으로 설정
      - 사용자 프로그램에 CPU를 넘기기 전에 mode bit을 1로 설정
    - Interrupt line
      - CPU가 메모리 이외의 다른 하드웨어와 통신할 수 있는 경로
        - CPU가 I/O (키보드 입력, 화면 출력 등)와 관련한 신호를 받는 경로
        - Timer
      - CPU가 여러 프로그램을 번갈아가며 실행하는 도중 체크

  - Memory

    - memory controller 존재
      - CPU와 DMA controller가 동시에 memory에 접근하는 것을 방지

  - Timer

    - 특정 프로그램이 무한루프에 빠지게 되면 CPU를 독점하게됨
    - 이를 방지하기 위해 프로그램 별로 실행 시간을 할당하여 CPU를 독점하는 것을 방지
      - 정해둔 시간이 지나면, timer가 CPU에 interrupt를 걸게되고, 운영체제가 CPU의 제어권을 가져감
    - 매 클럭 틱 마다 1씩 감소
    - 타이머 값이 0이 되면 interrupt 발생
    - 현재 시간 계산에도 활용

  - DMA controller

    - DMA가 memory에 접근할 수 있도록 해줌
    - DMA는 I/O 장치에 의해 너무 많은 interrupt가 발생하여 CPU의 효율이 떨어지는 것을 방지
      - DMA가 CPU 대신 local buffer의 내용을 memory에 복사하고 CPU에 interrupt를 걸어 I/O가 끝났음을 알림
      - 이를 통해 CPU가 interrupt 당하는 빈도를 줄임

    

- I/O device

  - device controller
    - CPU에 비해 I/O device는 매우 느리므로, 각각의 device를 전담하는 일종의 작은 CPU
      - 예를들어, disk의 내부를 통제하는 것은 CPU가 아니고 disk controller의 역할
    - local buffer
      - device controller의 작업 공간
      - I/O는 실제 device와 local buffer 사이에서 일어남
    - device controller는 I/O가 끝났을 경우 interrupt를 통해 CPU에 그 사실을 알림
  - device driver
    - OS 코드 중 각 device에 접근하기 위한 software
  - Disk
    - Input/Output device의 역할 동시 수행
  - Mouse, Keyboard, ...



## 입출력 (I/O)의 수행

- 모든 입출력 명령은 모니터 모드에서만 수행가능한 특권 명령
- 시스템 콜 (System Call)
  - 사용자 프로그램이 운영 체제의 서비스를 받기 위해 커널 함수를 호출하는 것
  - 사용자 프로그램은 운영체제에게 I/O를 요청
    - 요청에 따라 사용자 모드에서 모니터 모드로 넘어감
      - Mode bit을 1에서 0으로 바꿈
    - Trap(소프트웨어적 interrupt)을 사용하여 interrupt 벡터의 특정 위치로 이동
    - 제어권이 interrupt 벡터가 가리키는 interrupt 서비스 루틴으로 이동
    - 올바른 I/O 요청인지 확인 후 I/O 수행
    - I/O 완료 시 제어권을 시스템 콜 다음 명령으로 옮김
    - I/O를 위해서는 두 가지 interrupt가 모두 걸림
      - I/O 요청 -> trap
      - I/O 완료 -> interrupt



## 인터럽트(Interrupt)

- 인터럽트 당한 시점의 레지스터와 program counter를 save한 후, CPU의 제어를 인터럽트 처리 루틴에 넘기게 됨
- Interrupt (하드웨어 interrupt)
  - 하드웨어(I/O device 등)가 발생시킨 인터럽트
- Trap (소프트웨어 interrupt)
  - Exception
    - 프로그램이 오류를 범한 경우
  - System call
    - 프로그램이 커널 함수를 호출하는 경우
- Interrupt 벡터
  - 해당 interrupt의 처리 루틴 주소를 가지고 있음
- Interrupt 처리 루틴 (Interrput Service Routine, Interrupt Handler)
  - 각각의 interrupt 마다 운영 체제가 해야하는 일이 다름
    - 키보드 컨트롤러가 interrupt를 걸면, local buffer의 내용을 memory에 복사하고, 키보드 I/O를 요청했던 프로세스에는 CPU를 얻을 수 있다고 알려야함
    - Timer가 interrupt를 걸면, CPU를 뺐어서 다른 프로레스에 넘겨야함
  - 각각의 interrupt를 처리하는 커널 함수
    - interrupt 마다 해야하는 일이 운영 체제의 코드에 미리 정의되어 있음
- 현대의 운영 체제는 interrupt에 의해 구동됨
  - 운영 체제는 평소에 CPU를 사용할 일이 없음
  - 항상 사용자 프로그램이 운영 체제 사용
  - interrupt가 걸릴 때만 CPU가 운영 체제로 넘어감




