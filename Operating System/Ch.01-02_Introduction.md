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