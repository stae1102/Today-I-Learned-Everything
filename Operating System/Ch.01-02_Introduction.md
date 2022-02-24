> 인프런 주니온 교수님의 '운영체제 공룡책 강의'를 참고하며

- [운영체제가 뭐길래?](#운영체제가-뭐길래)
  - [컴퓨터는 무엇인가?](#컴퓨터는-무엇인가)
  - [정보가 무엇인가?](#정보가-무엇인가)
  - [컴퓨터가 정보를 어떻게 처리하죠?](#컴퓨터가-정보를-어떻게-처리하죠)
  - [그래서, 컴퓨터가 정보를 어떻게 처리하죠?](#그래서-컴퓨터가-정보를-어떻게-처리하죠)
  - [컴퓨터가 만능이라는 건가요?](#컴퓨터가-만능이라는-건가요)
  - [컴퓨터는 누가 만들었어요?](#컴퓨터는-누가-만들었어요)
  - [앨런 튜링이 왜 컴퓨터의 할아버지인가요?](#앨런-튜링이-왜-컴퓨터의-할아버지인가요)
  - [폰 노이만이 왜 컴퓨터의 아버지인가요?](#폰-노이만이-왜-컴퓨터의-아버지인가요)
  - [프로그램이 뭔데요?](#프로그램이-뭔데요)
  - [운영체제도 프로그램인가요?](#운영체제도-프로그램인가요)
  - [운영체제가 뭔가요?](#운영체제가-뭔가요)
- [운영체제의 개념과 구조: Chapter 1-2. Introduction& O/S structures](#운영체제의-개념과-구조-chapter-1-2-introduction-os-structures)
  - [1.1 What Operating Systems Do](#11-what-operating-systems-do)
    - [운영체제의 정의](#운영체제의-정의)
    - [컴퓨터의 4개의 컴포넌트](#컴퓨터의-4개의-컴포넌트)
    - [운영체제의 정의](#운영체제의-정의-1)
  - [1.2 Computer-System Organization](#12-computer-system-organization)
    - [전통적인 컴퓨터의 모양(Classical computer system)](#전통적인-컴퓨터의-모양classical-computer-system)
    - [부트스트랩 프로그램](#부트스트랩-프로그램)
    - [Interrupts](#interrupts)
    - [폰 노이만 아키텍쳐](#폰-노이만-아키텍쳐)
    - [storage system](#storage-system)
    - [I/O Structure](#io-structure)
  - [1.3 Computer System Architecture](#13-computer-system-architecture)
    - [컴퓨터 시스템 컴포넌트의 정의](#컴퓨터-시스템-컴포넌트의-정의)
    - [Symmetric multiprocessing (SMP)](#symmetric-multiprocessing-smp)
    - [Multi-core design](#multi-core-design)
  - [1.4 Operating System Operations](#14-operating-system-operations)
    - [Multiprogramming](#multiprogramming)
    - [Multitasking(= multiprocessing)](#multitasking-multiprocessing)
    - [Two separate mode of operations:](#two-separate-mode-of-operations)
  - [1.7 Virtualization](#17-virtualization)
    - [Virtualization이란](#virtualization이란)
  - [1.10 Computing Environments](#110-computing-environments)
    - [Operating Systems in the Variety of Computing Environments](#operating-systems-in-the-variety-of-computing-environments)
  - [2.1 Operating System Services](#21-operating-system-services)
    - [OS provides an environment for the execution of programse](#os-provides-an-environment-for-the-execution-of-programse)
  - [2.2 User and Operating-System Interface](#22-user-and-operating-system-interface)
    - [Three fundamental ways for users to interface with the OS:](#three-fundamental-ways-for-users-to-interface-with-the-os)
  - [2.3 System Calls](#23-system-calls)
    - [System calls](#system-calls)

# 운영체제가 뭐길래?

## 컴퓨터는 무엇인가?

* A computer is a machine that process the "information."

* 계산기 - 계산기이지만, 스마트폰은 컴퓨터라고 할 수 있음.

## 정보가 무엇인가?

* An information can be defined as a quantitative representation that measures the uncertainty

* 정보는 불확실성을 측정하여 수치적으로 표현한 것이다.

## 컴퓨터가 정보를 어떻게 처리하죠?

* 정보의 최소 단위: bit(binary digit)
* 정보의 처리: 정보의 상태 변환(0에서 1로, 1에서 0으로)
* 불리언 대수(Boolean Algebra): NOT, AND, OR
* 논리 게이트: NOT, AD, OR, XOR, NAND, NOR
* 논리 회로: IC, LSI, VLSI, ULSI, SoC, ......
  - 무어의 법칙, 황의 법칙
* 정보의 저장과 전송: 플립-플롭, 데이터 버스

## 그래서, 컴퓨터가 정보를 어떻게 처리하죠?

* 덧셈은? 반가산기, 전가산기
* 뺄셈은? 2의 보수 표현법
* 곱셈과 나눗셈은? 덧셈과 뺄셈의 반복
* 실수 연산은? 부동 소수점 표현법
* 함수는? GOTO
* 삼각함수, 미분, 적분, 사진 촬영, 동영상 재생, ......

## 컴퓨터가 만능이라는 건가요?

* 범용성: universality
  - NOT, AND, OR 게이트만으로 모든 계산을 할 수 있다.
  - NAND 게이트만으로 모든 계산을 할 수 있다.
  - 범용 컴퓨터: general-purpose computer

* 계산가능성: computability
  - Turing-computable: 튜링 머신으로 계산 가능한 것.
  - 정지 문제: Halting Problem: 튜링 머신으로 풀 수 없는 문제.

## 컴퓨터는 누가 만들었어요?

* 컴퓨터의 할아버지
  - Alan Turing - Turing Machine

* 컴퓨터의 아버지
  - John von Neumann - ISA: Instruction Set Architecture
  
## 앨런 튜링이 왜 컴퓨터의 할아버지인가요?

* Head, Tape, Turing Machines, *Universal Turing Machine*
  - 헤드와 페이프가 있으면 튜링머신을 만들 수 있는데, 이 튜링머신으로 유니버셜 튜링머신을 만들 수 있다.(현대적 컴퓨터의 원형)
* CPU, RAM, Application Programs, *Operating System*(현대적 컴퓨터)

## 폰 노이만이 왜 컴퓨터의 아버지인가요?

* A stored-program computer is a computer that stores programs in a memory.(폰 노이만 아키텍쳐)
* 내장형 프로그램 방식을 처음으로 도입
* 메모리에 프로그램을 저장
* fetch & execute

## 프로그램이 뭔데요?

* A program is a sef of instructions that tells a computer's hardware to perform a task.

* 컴퓨터의 하드웨어에게 태스크를 전달하는 명령어들의 집합이다.

## 운영체제도 프로그램인가요?

* Operating System
  - is a program running at all times on the computer
  - to provide system services to application programs
  - to manage process, resources, user interfaces, and so on.

* 컴퓨터 위에서 항상 실행되고 있는 프로그램이며, 어플리케이션 프로그램에게 시스템 서비스를 제공의 역할을 하며, 프로세스와 리소스(파일, 프린터 등), 유저 인터페이스(마우스, 키보드 등) 등을 관리한다.

## 운영체제가 뭔가요?

* An operating system is a software that operate a computer system.

* 소프트웨어로 컴퓨터 시스템을 운영한다.

# 운영체제의 개념과 구조: Chapter 1-2. Introduction& O/S structures


## 1.1 What Operating Systems Do

### 운영체제의 정의

* 컴퓨터 하드웨어를 제어하는 소프트웨어

* 어플리케이션 프로그램의 기반을 제공하며 컴퓨터 유저와 컴퓨터 하드웨어의 사이에서 중간 매개체 역할을 해준다.

### 컴퓨터의 4개의 컴포넌트

* 하드웨어
* 운영체제
* 어플리케이션 프로그램
* 유저

![컴퓨터 시스템의 컴포넌트](Fig%201.1.jpg)  

### 운영체제의 정의

* 운영체제의 정의는 정해진 것이 없다.
* 일반적인 정의는 '항상 컴퓨터에서 작동하는 프로그램 하나'라고 하며 **커널(kernel)** 이라고 한다.
* 커널에서 시스템 프로그램과 어플리케이션 프로그램에 대한 인터페이스를 제공해준다.
* 커널이 O/S의 핵심부분을 담당한다.

## 1.2 Computer-System Organization

### 전통적인 컴퓨터의 모양(Classical computer system)

![전통적인 컴퓨터 시스템](Fig%201.2.jpg)  

* 한개 이상의 CPU를 가지며 여러 개의 디바이스 컨트롤러와 버스(bus)를 통해서 연결되어 있다.(삽화 속 각 부품을 이은 선을 bus라고 생각)

### 부트스트랩 프로그램

* 부트스트래핑은 전원을 인가했을 때 처음으로 해야 할 프로그램이다.(롬에 저장되어 있으며 메모리에 운영체제를 로딩해주는 역할을 해야 함.)

* HDD에 있는 운영체제(커널)을 로드하여 메모리에 로드한다.

* 그 이후에는 운영체제에서 메모리에 응용프로그램을 운영

### Interrupts

![Interrupts](Fig%201.3.jpg)  

* 간단히 생각해서 CPU와 I/O device가 상호작용하는 것
* 하드웨어(Hardware)가 버스를 통해 언제라도 인터럽트(Interrupt)를 작동시킬 수 있다
* by sending a signal to the CPU, usually by way of the system bus.

### 폰 노이만 아키텍쳐

* 전형적인 명령 수행 사이클, 명령어 집합으로 구성된 컴퓨터 프로그램을 메모리에 로딩하면 메모리에 있는 명령어를 CPU가 하나씩 페치(fetch)하고 CPU가 execute 하는 사이클을 폰 노이만 아키텍쳐라고 부른다.

* 그러기 위해서는 명령어 레지스터(instruction register, IR)에 명령어를 저장한다.

### storage system

* 용량에 따라, 접근 속도에 따라 여러 개의 계층으로 구성되어 있는데, 가장 상위가 CPU에 있는 Register이고 그 다음이 cache이고, 그 다음이 램(main memory), SSD(solid-state disk, 메모리 형대의 저장소), HDD(hard disk), ...

### I/O Structure

![I/O Structure](Fig%201.7.jpg)  

* DMA: Directed Memory Access. CPU를 거치지 않고 디바이스와 메모리가 서로 주고 받는 과정(인터럽트 구조)

* OS 코드는 I/O 관리가 가장 중요한 부분이다.

## 1.3 Computer System Architecture

### 컴퓨터 시스템 컴포넌트의 정의

* CPU - The hardware that executes instructions.
* Processor - A physical chip that contains one or more CPUs.
* Core - The back computation unit of the CPU.
* Multicore - Including multiple computing cores on the same CPU.
* Multiprocessor - Including multiple processors.

### Symmetric multiprocessing (SMP)

![SMP](Fig%201.8.jpg)  

* 메모리에 연결되어 있는 CPU가 여러 개가 각각의 register와 cache를 갖고 있는 것.

### Multi-core design

![Multi-core design](Fig%201.9.jpg)  

* CPU 하나의 칩(Processor chip) 안에 register와 cache를 가지는 코어를 여러 개를 둔 것(듀얼 코어, 쿼드 코어, 옥타 코어)

* Multi-core cpu가 여러 개 붙으면 Multi-processor

## 1.4 Operating System Operations

### Multiprogramming

![Multiprogramming](Fig%201.12.jpg)

* 프로그램을 한 개 이상 구동하는 것

* 메모리에서 여러 개의 프로세스를 동시에 유지하는 것

* CPU 사용 효율을 높일 수 있음

### Multitasking(= multiprocessing)

* 하나의 CPU에서 여러 개의 프로세스를 자주 바꿔주면 여러 개의 프로세스를 동시에 작동하는 것처럼 유저가 인식하게 하는 과정

* concurrency, pallelism

* CPU scheduling
  * 멀티태스킹을 함에 앞서 cpu 효율을 제일 좋게 만드는 선택하는 방법

### Two separate mode of operations:

![Two models](Fig%201.13.jpg)

* user mode and kernel mode

* 부적절하게 다른 프로그램을 야기하지 않도록 막아주는 역할을 운영체제가 해야 한다.

* 커널 모드와 유저 모드를 분할하면 커널 모드에서만 할 수 있는 과정을 수행하도록 하여 O/S를 제외한 user 프로그램은 하드웨어를 제어하지 못함.

## 1.7 Virtualization

### Virtualization이란

* 하나의 컴퓨터의 하드웨어에서 여러 개의 다른 수행 환경을 끌어내는 것.

* VMM: Virtual Machine Manager
  - VMware, XEN, WSL, and so on.

![Virtualization](Fig%201.16.jpg)  

## 1.10 Computing Environments

### Operating Systems in the Variety of Computing Environments

* 전통 컴퓨팅
* 모바일 컴퓨팅
* Client-Server 컴퓨팅(ex. 웹 브라우저&웹 서버)
* Peer-to-Peer Computing(ex. 음악 파일 공유, BitTorrent, BitCoin, BlockChain)
* Cloud Computing(ex. AWS, Azure, GCP)
* Real-Time Embedded Systems

## 2.1 Operating System Services

### OS provides an environment for the execution of programse

컴퓨터 프로그램이 실행되리 수 있는 환경을 제공해주는 OS

* User interface
* Program execution
* I/O operation
* File-system manipulation
* Communications
* Error detection
* Resource allocation
* Logging
* Pretection and security

![OS services](Fig%202.1.jpg)

## 2.2 User and Operating-System Interface

### Three fundamental ways for users to interface with the OS:

* CLI: command line interface, or command interpreter
  - shells: sh, bash, csh, ...

* GUI: graphical user interface
  - Windows, MacOS, Linux, ...

* Touch-Screen Interface
  - Android, iOS, ...

## 2.3 System Calls

### System calls
실제로 컴퓨터 응용 프로그램은 os와 어떻게 interface 하는가? - system calls  

* API: Application Programming Interface
  - O/S의 API가 system calls

![system call](Fig%202.6.jpg)

* ex. C 라이브러리