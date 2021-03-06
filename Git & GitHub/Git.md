```
본 정리는 「팀 개발을 위한 Git·GitHub시작하기」, 정호영, 한빛미디어
내용을 정리한 문서임을 밝힙니다.
```
# 목차
- [목차](#목차)
- [Chapter 0. Git, GitHub 감 익히기](#chapter-0-git-github-감-익히기)
  - [0-1. Git 설치 및 로컬저장소에서 커밋 관리](#0-1-git-설치-및-로컬저장소에서-커밋-관리)
    - [0-1-1. 로컬저장소 만들기](#0-1-1-로컬저장소-만들기)
    - [0-1-2. 첫 번째 커밋 만들기](#0-1-2-첫-번째-커밋-만들기)
    - [0-1-3. 다른 커밋으로 시간 여행하기](#0-1-3-다른-커밋으로-시간-여행하기)
  - [0-2. GitHub 원격저장소에 커밋 올리기](#0-2-github-원격저장소에-커밋-올리기)
    - [0-2-1. 원격저장소에 커밋 올리기](#0-2-1-원격저장소에-커밋-올리기)
  - [01-3. GitHub 원격저장소의 커밋을 로컬저장소에 내려받기](#01-3-github-원격저장소의-커밋을-로컬저장소에-내려받기)
    - [0-3-1. 원격저장소의 커밋을 로컬저장소에 내려받기](#0-3-1-원격저장소의-커밋을-로컬저장소에-내려받기)
    - [0-3-2. 원격저장소의 새로운 커밋을 로컬저장소에 갱신하기](#0-3-2-원격저장소의-새로운-커밋을-로컬저장소에-갱신하기)
  - [0-4. 정리·복습](#0-4-정리복습)
- [Chapter 1. GUI 환경에서 버전 관리하기](#chapter-1-gui-환경에서-버전-관리하기)
  - [1-1. GitHub 둘러보기](#1-1-github-둘러보기)
    - [1-1-1. GitHub 원격저장소 생성 화면](#1-1-1-github-원격저장소-생성-화면)
    - [1-1-2. GitHub의 다양한 활용법](#1-1-2-github의-다양한-활용법)
- [Chapter 2. 혼자서 Git으로 버전 관리하기](#chapter-2-혼자서-git으로-버전-관리하기)
  - [2-1. Git 뜯어보기](#2-1-git-뜯어보기)
    - [2-1-1. 커밋은 Delta(차이점)가 아니라 Snapshot(스냅사진)](#2-1-1-커밋은-delta차이점가-아니라-snapshot스냅사진)
    - [2-1-2. Git으로 관리하는 파일의 4가지 상태](#2-1-2-git으로-관리하는-파일의-4가지-상태)
- [Chapter 3. 여러 명이 함께 Git으로 협업하기](#chapter-3-여러-명이-함께-git으로-협업하기)
  - [3-1. 원격저장소에서 협업하기: 브랜치(Branch)](#3-1-원격저장소에서-협업하기-브랜치branch)
    - [3-1-1. Git이 커밋을 관리하는 방식: 줄줄이 기차](#3-1-1-git이-커밋을-관리하는-방식-줄줄이-기차)
    - [3-1-2. 브랜치](#3-1-2-브랜치)
  - [3-2. 브랜치 실습 기본: 만들고, 이동한다](#3-2-브랜치-실습-기본-만들고-이동한다)
    - [3-2-1. 새 브랜치 만들기](#3-2-1-새-브랜치-만들기)
    - [3-2-2. 브랜치 이동하기: 체크아웃(checkout)](#3-2-2-브랜치-이동하기-체크아웃checkout)
  - [3-3. 브랜치와 브랜치를 합치기: 병합(merge, 머지)](#3-3-브랜치와-브랜치를-합치기-병합merge-머지)
    - [3-3-1. 병합은 무엇인가요?](#3-3-1-병합은-무엇인가요)
    - [3-3-2. 두 브랜치를 합치는 과정](#3-3-2-두-브랜치를-합치는-과정)
  - [* Git에서 브랜치와 브랜치를 합치는 명령어는 머지(merge)인데, 우리말로 병합이라고 부른다. 앞서 살펴봤듯이 각각 다른 브랜치에서 개발을 완료했기 때문에 각자 만든 두 개의 브랜치를 base 브랜치에 합쳐야 한다.](#-git에서-브랜치와-브랜치를-합치는-명령어는-머지merge인데-우리말로-병합이라고-부른다-앞서-살펴봤듯이-각각-다른-브랜치에서-개발을-완료했기-때문에-각자-만든-두-개의-브랜치를-base-브랜치에-합쳐야-한다)
  - [3-4. 앗! 둘이 똑같은 코드를 고쳤어요: 충돌(conflict) 해결하기](#3-4-앗-둘이-똑같은-코드를-고쳤어요-충돌conflict-해결하기)
    - [3-4-1. 브랜치 합치기 실습: 병합 커밋 및 충돌 해결](#3-4-1-브랜치-합치기-실습-병합-커밋-및-충돌-해결)
      - [병합 충돌 발생](#병합-충돌-발생)
  - [3-5. 브랜치를 합치는 예의바른 방법: 풀 리퀘스트](#3-5-브랜치를-합치는-예의바른-방법-풀-리퀘스트)
    - [3-5-1. 풀 리퀘스트 만들기](#3-5-1-풀-리퀘스트-만들기)
  - [3-6. 개발이 완료되었습니다, 출시하자!: 릴리즈(release)](#3-6-개발이-완료되었습니다-출시하자-릴리즈release)
    - [3-6-1. 프로그램의 버전(version)이란?](#3-6-1-프로그램의-버전version이란)
    - [3-6-2. 특정 커밋에 포스트잇 붙이기 - 태그(tag)](#3-6-2-특정-커밋에-포스트잇-붙이기---태그tag)
- [Chapter 4. 둘 이상의 원격저장소로 협업하기](#chapter-4-둘-이상의-원격저장소로-협업하기)
  - [4-1. 원본저장소를 복사해서 너구리의 원격저장소를 만든다(fork)](#4-1-원본저장소를-복사해서-너구리의-원격저장소를-만든다fork)
    - [4-1-1. 평행세계를 만드는 브랜치(branch), 평행우주를 만드는 포크(fork)](#4-1-1-평행세계를-만드는-브랜치branch-평행우주를-만드는-포크fork)
    - [4-1-2. 남의 저장소를 내 계정에 통째로 복제하기(Fork)](#4-1-2-남의-저장소를-내-계정에-통째로-복제하기fork)
  - [4-2. 원본저장소에 풀 리퀘스트 보내기](#4-2-원본저장소에-풀-리퀘스트-보내기)
    - [4-2-1. 포크한 원격저장소에서 원본저장소로 풀 리퀘스트 보내기](#4-2-1-포크한-원격저장소에서-원본저장소로-풀-리퀘스트-보내기)
    - [4-2-2. 풀 리퀘스트를 승인하고, 병합하기](#4-2-2-풀-리퀘스트를-승인하고-병합하기)
  - [4-3. 묵은 커밋을 새 커밋으로 이력 조작하기(rebase)](#4-3-묵은-커밋을-새-커밋으로-이력-조작하기rebase)
    - [4-3-1. 원본저장소에 새로운 커밋이 있는데, 포크한 내 원격저장소에는 안 보여요!](#4-3-1-원본저장소에-새로운-커밋이-있는데-포크한-내-원격저장소에는-안-보여요)
    - [4-3-2. 여러 원격저장소 히스토리를 한 눈에 보기: 리모트 추가(Add remote)](#4-3-2-여러-원격저장소-히스토리를-한-눈에-보기-리모트-추가add-remote)
    - [4-3-3. 묵은 커밋을 방금 한 커밋처럼: 리베이스(Rebase)](#4-3-3-묵은-커밋을-방금-한-커밋처럼-리베이스rebase)
- [Chapter 5. 실무 사례와 함께 Git 배우기](#chapter-5-실무-사례와-함께-git-배우기)
  - [5-1. 실습을 위한 사전 준비: 새로운 원격저장소 만들기](#5-1-실습을-위한-사전-준비-새로운-원격저장소-만들기)
  - [5-2. amend: 수정 못한 파일이 있어요, 방금 만든 커밋에 추가하고 싶어요.](#5-2-amend-수정-못한-파일이-있어요-방금-만든-커밋에-추가하고-싶어요)
    - [5-2-1. amend로 마지막 커밋 수정하기](#5-2-1-amend로-마지막-커밋-수정하기)
    - [5-2-2. amend로 마지막 커밋 메시지를 수정하고 원격저장소 브랜치에 강제 푸시하기](#5-2-2-amend로-마지막-커밋-메시지를-수정하고-원격저장소-브랜치에-강제-푸시하기)
  - [5-3. cherry-pick: 저 커밋 하나만 떼서 지금 브랜치에 붙이고 싶어요.](#5-3-cherry-pick-저-커밋-하나만-떼서-지금-브랜치에-붙이고-싶어요)
    - [5-3-1. cherry-pick: 다른 브랜치의 커밋 하나만 내 브랜치에 반영하기](#5-3-1-cherry-pick-다른-브랜치의-커밋-하나만-내-브랜치에-반영하기)
  - [5-4. reset: 옛날 커밋으로 브랜치를 되돌리고 싶어요](#5-4-reset-옛날-커밋으로-브랜치를-되돌리고-싶어요)
    - [5-4-1. Soft/Mixed reset: 모든 기억을 남기면서 브랜치를 되돌리기](#5-4-1-softmixed-reset-모든-기억을-남기면서-브랜치를-되돌리기)
    - [5-4-2. Hard reset: 모든 기억을 지우며 브랜치를 되돌리기](#5-4-2-hard-reset-모든-기억을-지우며-브랜치를-되돌리기)
  - [5-5. revert: 이 커밋의 변경사항을 되돌리고 싶어요](#5-5-revert-이-커밋의-변경사항을-되돌리고-싶어요)
  - [5-6. stash: 변경 사항을 잠시 다른 곳에 저장하고 싶어요, 커밋은 안 만들래요](#5-6-stash-변경-사항을-잠시-다른-곳에-저장하고-싶어요-커밋은-안-만들래요)

# Chapter 0. Git, GitHub 감 익히기

## 0-1. Git 설치 및 로컬저장소에서 커밋 관리

### 0-1-1. 로컬저장소 만들기

* CLI를 통한 접근

1. 생성한 폴더에서 마우스 클릭하여 Git Bash Here 클릭
2. 혹은 CLI 환경을 통해 원하는 폴더로 이동

```
$ git init
```
을 통해 새롭게 로컬저장소를 만들 수 있다.  
  
이때, 폴더 속 .git 폴더가 생성되는데 .git 폴더 속에 Git으로 생성한 버전들의 정보와 원격저장소 주소 등이 들어있으며 이것은 **로컬저장소**라고 부른다.
  
> 일반 프로젝트 폴더에 'git init' 명령어(Git초기화 과정)를 통해 로컬 저장소를 만들면 그때부터 이 폴더에서 버전 관리를 할 수 있다.

### 0-1-2. 첫 번째 커밋 만들기

* Git에서는 생성된 각 버전을 **커밋(Commit)** 이라고 부른다.

> 커밋의 과정
> 1. 커밋에 추가할 파일을 선택
> ```
> $ git add file *.*
> ```
> 2. 커밋을 만들고 메세지 입력하지
> ```
> $ git commit -m "메시지"
> ```

### 0-1-3. 다른 커밋으로 시간 여행하기
  
* 개발을 하던 중 요구 사항이 바뀌어서 이전 커밋부터 다시 개발하고 싶다면 Git을 사용하여 그 때의 커밋으로 돌아갈 수 있다.
  
> 커밋 이동
> 1. log 확인하기
> ```
> $ git log
> ```
> 2. 로그 확인 후 커밋 아이디 7자리 입력하여 불러오기
> ```
> $ git checkout 1234567
> ```
> *최신 커밋으로 돌아가기*
> ```
> $ git checkout -
> ```

## 0-2. GitHub 원격저장소에 커밋 올리기

### 0-2-1. 원격저장소에 커밋 올리기
* GitHub에서 만든 원격저장소 주소를 로컬저장소에 알려주고, 로컬저장소에 만들었던 커밋들을 원격저장소에 업로드

> 커밋 업로드
> 1. Git Bash를 통해 원격저장소의 주소를 알리기
> ```
> $ git remote add origin htts://github.com/깃헙-아이디/레포지토리-이름.git
> ```
> 2. 로컬저장소에 있는 커밋들을 push 명령어로 원격저장소에 업로드
> ```
> $ git push origin master
> ```

* 이렇게 로컬저장소의 커밋을 원격저장소로 push 명령어를 사용해서 올리는 일을 **푸시한다**라고 한다.

## 01-3. GitHub 원격저장소의 커밋을 로컬저장소에 내려받기

### 0-3-1. 원격저장소의 커밋을 로컬저장소에 내려받기
* 원격저장소의 코드와 버전 전체를 내 컴퓨터로 내려받는 것을 **클론(Clone)** 이라고 한다.
* 클론을 하면 최신 버전뿐만 아니라 이전 버전들과 원격저장소 주소 등이 내 컴퓨터의 로컬저장소에 저장된다.

> 원격저장소의 커밋 로컬저장소에 내려받기
> 1. 로컬저장소에 새로운 폴더 생성 (Optional)
> 2. 새로 생성한 폴더에 Git Bash 접속
> 3. GitHub Repository 주소를 복사하여 클론
> ```
> $ git clone htts://github.com/깃헙-아이디/레포지토리-이름.git
> ```
> 4. 클론한 로컬저장소에 다운한 파일과 .git 폴더 확인

### 0-3-2. 원격저장소의 새로운 커밋을 로컬저장소에 갱신하기

> 원격저장소 커밋 로컬저장소에 갱신하기
> 1. 버전이 다른 커밋이 있는 로컬 저장소에서 Git Bash 접속
> 2. pull하여 원격저장소의 커밋 받아오기
> ```
> $ git pull origin master
> ```

## 0-4. 정리·복습

* Git : 깃이라고 읽고, 버전 관리 시스템
* GitHub : 깃허브라고 읽고, Git으로 관리하는 프로젝트를 올려둘 수 있는 사이트
* GUI : Graphic User Interface, 즉 마우스로 클릭해서 사용하는 방식
* CLI : Command Line Interface, 즉 명ㄹ영어를 하나씩 입력하는 방식
* Git Bash : CLI 방식으로 Git을 사용할 수 있는 환경
* 커밋 : 버전 관리를 통해 생성된 파일, 혹은 그 행위
* log 명령어 : 지금까지 만든 커밋을 모두 확인
* 체크아웃한다 : checkout으로 원하는 지점으로 파일을 되돌리기
* 로컬저장소 : Git으로 버전 관리하는 내 컴퓨터 안의 폴더를 의미
* 원격저장소 : GitHub에서 협업하는 공간(폴더)를 의미
* 레포지토리 : 원격저장소를 의미
* 푸시 : 로컬저장소의 커밋(버전 관리한 파일)을 원격저장소에 올리는 것
* 풀 : 원격저장소의 커밋을 로컬저장소에 내려받는 것

# Chapter 1. GUI 환경에서 버전 관리하기
* 소스트리, VScode 프로그램 설치

## 1-1. GitHub 둘러보기

### 1-1-1. GitHub 원격저장소 생성 화면

* Repository name : 저장소 이름(필수)
* Description : 저장소 간단 설명
* Public / Private : 공개 / 비공개 설정(필수)
* Initialize this repository with:
  * Add a README file : 빈 저장소가 아니고 README.md 파일이 담긴 저장소가 생성된다. 보통 저장소에 대한 설명 또는 설치 방법, 저장소에 기여한 사람 등 다양한 내용을 작성할 수 있다. GitHub에 접속한 후 저장소나 저장소 내부의 폴더에 들어오면 일부러 README.md 파일을 찾아 클릭하지 않아도, 첫 화면에 바로 표시된다.
  * Add .gitignore : 작업을 할 때 굳이 GitHub에 올릴 필요가 없는 파일이 있다. 이 옵션에서 선택한 항목에 따라 해당 프로젝트에서 GitHub에 올리지 않기를 바라는 파일이 자동으로 목록에 추가된다. 추후에도 얼마든지 .gitignore 파일을 만들 수 있다.
  * Choose a license : 공개적으로 사용하고, 다른 사용자도 참여하도록 만들어진 오픈소스에도 지적 재산권을 부여할 수 있다. MIT, Apache 2.0, GPLv3 등의 라이센스 문서 파일을 추가할 수 있으며, 이들은 저작권 명시를 반드시 해야 한다든지, 상표권을 침해하지 말아야 한다든지 하는 차이가 있다. https://choosealicense.com/ 에서 프로젝트에 맞는 라이센스를 고를 수 있다. 이또한 .gitignore처럼 추후에 변경할 수 있다.

### 1-1-2. GitHub의 다양한 활용법
* 마음에 드는 저장소에 별(Star)로 호감을 표시하고, 요즘 떠오르는 오픈 소스 저장소를 explore 탭에서 훑어볼 수 있다. 또는, 내가 좋아하는 서비스를 만든 엔지니어를 팔로우(Follow)해서 어떤 다른 개발 활동을 하고 있는지 볼 수도 있다.

# Chapter 2. 혼자서 Git으로 버전 관리하기
> 대부분 GUI를 활용한 실습이기에 생략

* 앞서 사용된 **origin**이란 이름은 우리가 연결한 GitHub 원격저장소의 닉네임이다.
```
$ git remote add origin htts://github.com/깃헙-아이디/레포지토리-이름.git
```
* 위 명령어의 경우 origin이란 이름으로 원격저장소를 추가하라는 뜻. 만약 'git remote add myOrigin htts://github.com/깃헙-아이디/레포지토리-이름.git'라고 입력했다면 소스트리에서는 **[origin]** 이 아닌 **[myOrigin]** 이라는 이름으로 원격저장소의 닉네임이 보였을 것이다.
* **master**는 우리가 커밋을 올리는 '줄기'의 이름이다. 따로 줄기를 생성하지 않으면 Git은 master라는 기본 줄기에 커밋을 올린다.
* 종합하자면 **[master]** 는 내 컴퓨터 로컬저장소의 버전을, 앞에 origin이 붙은 **[origin/master]** 는 GitHub 원격저장소의 버전을 가리키는 것이다.

## 2-1. Git 뜯어보기

### 2-1-1. 커밋은 Delta(차이점)가 아니라 Snapshot(스냅사진)

* Git은 커밋에 바뀐 것만 저장하는 것이 아니라 전체 코드를 저장한다. 예를 들어 README.txt의 세 번째 라인에 '안녕'을 추가한 커밋이 있다면 Git은 추가한 세 번째 라인만 아니라 첫 번째 라인부터 전체를 저장한다는 것이다.

### 2-1-2. Git으로 관리하는 파일의 4가지 상태

> Git의 처리 과정
> 1. Git을 초기화하고 파일을 작성하면 그 파일은 한 번도 커밋되지 않았기에 파일 상태는 '추적 안됨(untracked)' 상태이다. 
> 2. 프로젝트 폴더 내 작업 공간이 아닌 .git 폴더가 존재하는 로컬저장소에 add 명령어를 통해 원하는 파일을 스테이지에 올린다. 이때, 파일 상태가 '추적 안됨'에서 '스테이지됨(staged)'으로 변경된다.
> 3. 스테이지에 있는 파일 전체를 commit 명령어를 통해 하나의 스냅샷, 즉 버전으로 생성한 후, 파일 상태가 '스테이지됨'에서 '수정 없음(unmodified)'으로 변경되었다.
> 4. 커밋이 로컬저장소에만 있으면 나밖에 버전 관리를 못하기 때문에 다른 사람도 함께 하기 위해 push 명령어를 사용해 원격저장소에 업로드한다.
> 5. 파일을 수정해서 '수정 없음'에서 '수정함(modified)'으로 변경하고, 파일을 새로 생성한다. 새로 만든 파일은 새로 만들었기 때문에 '추적 안됨'상태이다.
> 6. '수정 없음'인 파일은 이미 스테이지에 올라와있기 때문에 스테이지에 올릴 수 없음. 다른 파일은 수정하여 add 명령어로 로컬저장소에 올린다.
> 7. 커밋을 통해 스냅샷을 만든다. 이 커밋은 앞서 만든 커밋에 연결되어 있다. 그래서 앞 커밋에 비해 이번 커밋은 파일이 수정되었고, 새 파일이 추가되었음을 Git이 계산을 통해 알아낼 수 있다.
> 8. push까지 마무리 해주면 새로 만든 하나의 커밋 또한 원격저장소에 올라가게 된다. 이로써 원하는 버전 관리를 성공시킬 수 있었다.

**종합하자면, Git으로 관리하는 파일은 '추적 안됨', '수정 없음', '수정함', '스테이지됨'의 총 네 가지 상태를 가지게 된다.**

# Chapter 3. 여러 명이 함께 Git으로 협업하기

## 3-1. 원격저장소에서 협업하기: 브랜치(Branch)

### 3-1-1. Git이 커밋을 관리하는 방식: 줄줄이 기차
  
* 코드의 변경사항을 묶어 하나의 덩러리로 만드는 것을 익혔습니다. 이것을 커밋이라고 했고, 새로 만든 커밋은 기존 커밋 다음에 시간순으로 쌓인다.
  
* *하지만 두 명이 협업한다면 어떻게 해야 할까?*
  * 한 줄로는 커밋을 이어나가지 못한다 새로운 두 커밋 모두 기준 커밋과 연결되어야 하기 때문에
  * 그렇기에 자연스레 두 줄로 갈래가 나뉘게 된다.

* 이렇게 특정 기준에서 줄기를 나누어 작업할 수 있는 기능을 **브랜치(Branch)** 라고 한다.
  
### 3-1-2. 브랜치

* 보통 브랜치를 문장으로 나타낼 때, 브랜치를 올린다고 하지 않고 브랜치에 커밋을 '가리킨다'라고 표현한다.
* 이것은 브랜치가 나뭇가지처럼 물리적으로 '길'이 존재해서 그 길에 올리는 것이 아니라 단순한 '포인터(pointer)'이기 때문이다.
* 순서대로 커밋1, 커밋2, 커밋3을 만들었다고 해보자. 새로 커밋을 할 때마다 [master] 브랜치의 포인터가 최신 커밋을 가리킨다. 커밋2를 가리키고 있던 [master] 브랜치에서 새로 커밋을 올리면 [master] 브랜치가 커밋3을 가리키도록 움직인다.

  * 커밋3의 상태에서 새로운 [고양이] 브랜치를 만들어 보겠다. 커밋 3에서 만든 브랜치니 [master] 브랜치와 동일하게 커밋3을 가리킬 것이다. 현재 [고양이] 브랜치와 [master] 브랜치의 상태는 모두 커밋3이다.
  
  * [고양이] 브랜치에 커밋을 하나 더 하면 [고양이] 브랜치가 [master] 브랜치보다 커밋 하나만큼 앞서게 된다.
  
  * 그 상태에서 [master] 브랜치로 이동해 커밋을 하나 더 하면, 이제는 [고양이] 브랜치와 [master] 브랜치의 버전이 눈에 띄게 갈라지게 된다. 커밋3을 기준(base)으로 두 가지 버전이 생긴 것이다. 그럼 내 컴퓨터에서 이 [고양이] 브랜치와 [master] 브랜치 사이를 어떻게 넘나들 수 있을까?
  
  * **[HEAD]** 라는 특수한 포인터가 그 비법이다. 브랜치 혹은 커밋을 가리키는 포인터이다. 우리는 [HEAD]를 이용해서 브랜치 사이를 마음대로 넘나들 수 있다. [HEAD] 포인터가 [master] 브랜치가 가리키는 커밋을 가리키고 있을 때는 그 커밋의 상태를 보여주지만, [고양이] 브랜치가 가리키는 커밋을 가리키면 그 커밋의 상태를 보여주게 된다.(브랜치를 가리키기 때문)
  
  * 브랜치의 최신 커밋이 아닌 과거 커밋으로도 [HEAD]를 이동시킬 수 있다. 다만 이 경우에는 [master] 브랜치의 포인터와 [HEAD]가 떨어져있기에 **'분리된 HEAD(Detached HEAD)'** 상태가 된다.

## 3-2. 브랜치 실습 기본: 만들고, 이동한다

### 3-2-1. 새 브랜치 만들기

* 본 실습은 GUI 실습이기 때문에 일부 생략

* 기존 HEAD가 가르치던 master브랜치에서 새 브랜치를 만들고 새로 커밋하게 되면 분기가 나누어지게 된다.

* 그 상태로 푸시하게 되면 원격저장소인 GitHub에도 적용되어 브랜치가 올라온 것을 볼 수 있다.

### 3-2-2. 브랜치 이동하기: 체크아웃(checkout)

* 체크아웃을 통해 브랜치를 이동할 수 있으며, 이를 통해 커밋이 병렬적으로 잘 생성될 수 있도록 할 수 있다.

* 그렇지 않고 계속해서 브랜치를 만들면 서로 다른 수정본이 모두 반영되게 된다.

* 즉, 브랜치를 만들 때는 base 브랜치를 잘 설정하고, checkout을 통해 설정해야 한다.

* 이 상태로 브랜치를 새로 생성하게 되면 본격적으로 나뭇가지처럼 가지를 뻗을 수 있게 된다.

* 각자의 개발이 완료되면 base 브랜치에 내 브랜치 작업물을 합치면 된다.

## 3-3. 브랜치와 브랜치를 합치기: 병합(merge, 머지)

### 3-3-1. 병합은 무엇인가요?
* **병합(merge)** 은 간단히 두 버전의 합집합을 구하는 것이다.
  1. Merge commit(병합 커밋) : 새로운 커밋
  2. Fast-forward(빨리 감기) : 기존 커밋에 내용 변경
  3. Conflict(충돌) : 뭘 커밋해야 할지 모르는 상황

### 3-3-2. 두 브랜치를 합치는 과정
* Git에서 브랜치와 브랜치를 합치는 명령어는 머지(merge)인데, 우리말로 병합이라고 부른다. 앞서 살펴봤듯이 각각 다른 브랜치에서 개발을 완료했기 때문에 각자 만든 두 개의 브랜치를 base 브랜치에 합쳐야 한다.
---
* 앞서 나눴던 브랜치를 예로 들자면
> * base 브랜치[master]-커밋2에 feature/detail-page-커밋4를 먼저 합치고자 한다. 이 커밋은 이전 커밋을 단순하게 수정한 최신본이기 때문에 두 상태를 합치면 따로 바뀌는 상태 없이 커밋4가 될 것이다.
> 
> * 커밋2를 가리키고 있던 [master] 브랜치가 빨리 감기를 해서 커밋4를 가리키게 되었다. 새로 추가되거나 충돌나는 것 없이 그냥 앞으로 이동하기만 하면 되어서 '빨리 감기'라고 부른다. 이제 [master] 브랜치는 [feature/detail-page] 브랜치의 새로운 코드가 반영된 버전이 되었다.
> 
> * [feature/detail-page] 브랜치의 모든 내용이 [master] 브랜치에 반영되었으니 [feature/detail-page] 브랜치는 삭제한다.
> 
> * 하지만, [feature/cart] 브랜치에서의 커밋은 [master] 브랜치가 가리키는 커밋4와 [feature/cart] 브랜치가 가리키는 커밋5는 커밋2를 중심으로 상태가 바뀌었기 때문에 병합 커밋이 될 것이다. 커밋4와 커밋5를 합치는 병합 커밋을 만드는 것이다.
> * 두 브랜치를 합치면서 새로운 병합 커밋은 둘 중 어디든 올릴 수 있으니 상황에 따라 선택하면 된다.

## 3-4. 앗! 둘이 똑같은 코드를 고쳤어요: 충돌(conflict) 해결하기

### 3-4-1. 브랜치 합치기 실습: 병합 커밋 및 충돌 해결
* 커밋3과 커밋4은 서로 다른 분기에 있어서 병합 커밋을 만들면서 코드를 합쳐야 한다.
* **꿀팁**: 혹시 병합하다 코드가 깨질 수 있으니 병합할 때는 다 같이 쓰는 브랜치 말고 내 전용 브랜치에서 먼저 병합하고 문제가 없는지 확인한다.
* 병합된 커밋이 문제가 없는 것을 확인하고 나서 병합 커밋을 브랜치에 반영한다.

#### 병합 충돌 발생
* 서로 다른 코드를 작성하여 병합 충돌이 발생할 수 있다.
```
<<<<<<< HEAD
3. 장바구니 담기
=======
3. 디테일 페이지 보여주기
>>>>>>> master
```

* 위처럼 베이스 브랜치인 [feature/cart] 브랜치의 코드가, 아래는 병합의 대상인 [master] 브랜치의 코드가 보인다.
* 이를 수정하기 위해서는 필요없는 텍스트를 모두 삭제한 후 `Crtl + S`로 저장
* 모든 충돌이 해결된 후 스테이지로 Add하고 최종적으로 커밋해준다.
* 이후 푸시하여 원격저장소에도 반영한다.
  
## 3-5. 브랜치를 합치는 예의바른 방법: 풀 리퀘스트

### 3-5-1. 풀 리퀘스트 만들기

* master 브랜치에 합치기 전에 이 브랜치에서 무엇을 바꾸었는지 협력자(Collaborators)가 확인할 수 있는 방법을 거쳐야 할 수 있다. 신입 개발자가 사수 개발자의 허락을 맡는 것과 같다.
* 이때, **풀 리퀘스트(Pull Request)** 가 필요하다. 협력자에게 브랜치 병합을 요청하는 메시지를 보내는 것이다.

> 1. 새 브랜치를 만든 후 새 파일을 만들고 스테이징 후 커밋, 푸시하여 원격저장소에 올린다.
> 
> 2. 이후 Compare & pull request 버튼을 클릭한다.
> 
>     1. base: master - 병합된 커밋이 들어갈 브랜치를 정하는 선택박스
> 
>     2. compare: feature/comment - 병합의 대상이 될, 즉 내가 만들어서 base 브랜치에 반영시키고 
> 싶은 브랜치
>     3. Able to merge - base 브랜치와 compare 브랜치가 충돌 없이 병합될 수 있다는 뜻. GitHub에서 
> 자동으로 계산해서 보여준다. 만약 충돌이 난다면 빨간색으로 Conflict가 있다고 보여진다.
>     4. 풀 리퀘스트 제목 - 동료 개발자가 한 눈에 이해하기 쉬운 제목을 적는다.
> 
>     5. 풀 리퀘스트 내용 - 동료 개발자가 코드를 이해하는 데 도움이 되는 설명을 적어준다. 
> 스크린샷을 첨부하거나 테스트하는 방법을 적을 수 있다.
>     6. Reviewers - 저장소의 협력자가 여러 명이라면 몇 명을 콕 찝어서 이 풀 리퀘스트를 검토해 달라 
> 요청할 수 있습니다. 보통 같은 팀원이나 해당 기능과 연관된 동료를 선택한다.
>     7. Assignees - 이 풀 리퀘스트를 담당하는 동료를 적어준다. 보통 자기 자신이다.
> 
>     8. Labels - 이 풀 리퀘스트에 관한 라벨을 달아준다. ex) [버그], [리뷰 필요], [프론트엔드], 
> [백엔드] 등
> 
> 3. 원격저장소에서 협력자가 이 풀 리퀘스트를 확인하고 새롭게 추가된 코드를 점검할 수 있다. 코드의 라인마다 댓글을 달 수 있어서 해당 코드가 왜 고쳐졌는지, 혹은 어떻게 개선할 수 있는지 풀 리퀘스트 내부에서 토론을 진행할 수 있다. 협력자는 이 풀 리퀘스트를 **수락(Accept)** 할 수 있고, 수정을 **요청(Request change)** 할 수 있으며, **병합(Merge pull request)** 할 수도 있다.
> 
> 4. Merge pull request 버튼을 누르면 병합 커밋을 만들 수 있는 입력창이 있는데, 입력할 메시지를 입력하고 **[Confirm merge]** 버튼을 클릭한다.
> 5. 닫힌 풀 리퀘스트는 [Pull Requests] 탭의 [Closed]에서 확인할 수 있다.
> 6. Git에서 새로운 이력을 업데이트 하는 명령은 [페치(fetch)]이다. 풀이 실제 코드를 내려받는 데 비해 페치는 그래프만 업데이트한다.
> 7. 내 컴퓨터의 [master] 브랜치에도 이 새로운 커밋을 반영하기 위하여 [master]로 브랜치를 옮긴다(checkout).
> 8. Pull하여 origin/master와 동일하게 커밋을 가리키도록 한다.

## 3-6. 개발이 완료되었습니다, 출시하자!: 릴리즈(release)

### 3-6-1. 프로그램의 버전(version)이란?

* 아이폰9, 포토샵 6.0, 7.0과 같이 제품이름에 버전명이 들어가 있는 것을 볼 수 있는데, Git에서 말하는 버전과도 비슷한 맥락으로, 의미 있는 특정 시점의 맥락을 말하는 것이다.
* 버전을 올리는 것은 크게 **메이저(Major)** 업그레이드와 **마이너(Minor)** 업그레이드로 나뉜다. 사용자들이 크게 느낄 변화를 적용했을 때 보통 메이저 버전을 올리고(v2.x → v3.x), 작은 변화 등이 생겼을 땐 마이너 버전을 올린다(v.2.3 → v.2.4).
* node.js의 경우 10.15.0 LTS 버전을 볼 수 있는데, 메이저 버전인 10, 마이너 버전인 15를 볼 수 있고, 그 뒤에 세 번째 버전이 있음을 알 수 있다. 이는 **메인터넌스(Maintenance)** 버전으로 버그나 유지보수 등 작은 수정이 들어갔을 때 바꾼다.

### 3-6-2. 특정 커밋에 포스트잇 붙이기 - 태그(tag)

* 프로그램을 출시하는 것을 **'릴리즈(release)'** 라고 한다. 병합을 마친 [master] 브랜치를 서버에 올려서 사용자들이 쓸 수 있도록 배포하고, 현재 코드 상태를 버전 v1.0.0이라고 기록하려고 한다. 이것은 **태그(tag)** 를 통해 간단하게 표시할 수 있다.

> 1. [master] 브랜치에 있는 상태에서 소스트리 상단의 [태그] 아이콘을 클릭하고 태그 이름을 'v1.0.0'이라고 적은 뒤 [태그 추가] 버튼을 클릭한다.
> 
> 2. [master] 브랜치 라벨 옆에 [v1.0.0] 라벨이 새로 붙은 것을 확인 할 수 있다. 브랜치와 비슷하게 생겼는데, 둘 다 커밋을 가리키는 가벼운 포인터이기 때문이다.
> 3. 만든 태그는 브랜치가 그랬던 것처럼 푸시를 해줘야 원격저장소에서도 볼 수 있다. 소스트리의 [Push] 아이콘을 눌러 팝업창을 띄우고 [모든 태그 푸시]라는 체크박스를 체크하고 [Push]를 클릭해서 태그를 원격저장소에 푸시한다.
> 4. GitHub의 원격저장소를 보면 [1 release]라고 표시된 탭이 있어 클릭한다.
> 5. 방금 만든 태그를 확인할 수 있고, [zip] 아이콘을 눌러 해당 태그가 가리키는 버전을 압축파일로 내려받을 수 있다.

# Chapter 4. 둘 이상의 원격저장소로 협업하기

## 4-1. 원본저장소를 복사해서 너구리의 원격저장소를 만든다(fork)

원본저장소에 바로 커밋을 올릴 권한이 없을 때, 원본저장소를 복사해서 본인의 GitHub에 새로운 원격저장소를 만들고, 이곳에서 커밋을 올리기로 한다. 새로운 원격저장소는 나만이 사용하는 공간으로 온갖 실험적인 커밋을 게시할 수 있다. 이렇게 남의 원본저장소를 내 계정의 원격저장소로 복사해오는 명령어는 **포크(fork)** 이다.

### 4-1-1. 평행세계를 만드는 브랜치(branch), 평행우주를 만드는 포크(fork)

* 기본적으로 원본저장소에 커밋을 직접 푸시할 수 있는 사람은 원본저장소를 만든 본인(소유자)뿐이다. 다른 사람이 이곳에 푸시하려면 원본저장소의 소유자가 이 사람을 협력자로 등록해야 한다. 원본저장소의 소유자가 협력자로 등록하려면 원본저장소의 메뉴에서 [Settings - Collaborators] 페이지에 들어가서 등록하려는 유저를 찾고, [Add collaborator]를 클릭하면 된다.

* 그런데 원본저장소의 소유자 입장에서는 협력자가 늘어날수록 원본저장소를 관리하기가 어려워진다. 협력자가 원본저장소에 직접 푸시할 수 있기 때문이다. 하지만, 동시에 많은 개발자에게 의견을 받고 오픈소스를 개선하고 싶은 니즈가 있다. 한편 개발자는 오픈소스에 참여하고 기여를 하고 싶어한다. 그렇지만 원본저장소에 직접 푸시하는 것은 부담이 생긴다.

* 이럴 때 대안디 될 수 있는 방법이 **풀 리퀘스트**이다. 개발자는 원본저장소를 자신의 계정에 복사(fork)해서 원격저장소를 생성하고, 이곳에 커밋을 올린 후 원본저장소의 소유자에게 병합요청을 하면 원본저장소의 소유자는 개발자의 병합 요청을 검토해서 원본저장소에 반영하는 것이다. *브랜치를 통해 코드 분기점을 만들고 풀 리퀘스트를 통해 서로 확인하고 병합하는 과정이랑 동일하다.*

* 포크는 브랜치를 포함한 원본저장소의 모든 커밋 이력을 새로운 원격저장소로 통째로 복사한다. 원본저장소의 이력을 보려면 추가적으로 이곳의 원격저장소 주소를 등록해야 한다.

### 4-1-2. 남의 저장소를 내 계정에 통째로 복제하기(Fork)

> 1. 새로 만든 계정을 통해 원본저장소에 접속하여 우측 상단 [Fork]버튼을 클릭하면 원본저장소가 내 계정에 복사된다.
> 
> 2. 포크되어 새롭게 만들어진 나으 원격저장소를 내 컴퓨터로 받아오기 위해 원격저장소의 주소를 복사한다.
> 
> 3. 소스트리에서 새탭을 생성하고 Clone을 클릭하여여 원격저장소의 주소를 입력한다.
> 
> 4. 원격저장소와 연결할 내 컴퓨터의 로컬저장소 폴더를 만들어서 선택한다.
> 
> 5. 세 번째 입력란에는 원하는 이름을 입력하고 [클론] 버튼을 클릭한다.
> 
> 6. 소스트리에 새로 로그인한다.
> 
> 7. 원하는 계정을 설정 초기화 텍스트를 클릭하여 기본 계정으로 전환한다. 
> 
> 8. 새 계정으로 커밋을 생성한 뒤 계정이 새 계정으로 되어있는지 확인한다.
>    * 만약 아니라면, 사람 아이콘을 클릭하고 '대체 작성자 정보 사용'에서 계정 정보를 넣어준다.
> 9. 커밋 후 Push하여 원격저장소에도 반영

## 4-2. 원본저장소에 풀 리퀘스트 보내기

### 4-2-1. 포크한 원격저장소에서 원본저장소로 풀 리퀘스트 보내기

> 1. GitHub 원격저장소에서 [New pull request] 버튼을 클릭한다.
> 
> 2. [head repository]에 내가 포크한 원격저장소가, [base repository]에 원본저장소가 보여지면 성공이다. 모든 정보가 확실하면 [Create pull request]버튼을 누릅니다. - 누르기 전에 아래의 변경 파일(changed files) 정보를 반드시 꼼꼼하게 확인할 것!
> 
> 3. 풀 리퀘스트에 대한 설명을 적습니다. [Create pull request] 버튼을 클릭한다.
> 
> 4. 성공적으로 풀 리퀘스트가 만들어졌으면, 풀 리퀘스트 승인(approve)과 병합(merge)을 기다리면 된다.
> 

### 4-2-2. 풀 리퀘스트를 승인하고, 병합하기

> 1. 원본저장소의 [Insights]탭을 클릭하고, 왼쪽의 [Forks]를 클릭하면 너구리가 포크했다는 것을 알 수 있다.
> 
> 2. [Pull requests]탭을 보면 1개의 풀 리퀘스트가 들어온 것을 확인할 수 있다.
> 
> 3. [File changed] 탭을 클릭하면 어떤 새로운 코드가 이 풀 리퀘스트에 담겨 있는지 확인할 수 있다. 변경된 코드의 왼쪽에서 [+] 플러스 버튼을 클릭해서 코드 라인별로 댓글을 달 수 있다. 여기에 수정사항을 제안하거나 질문할 수 있다. 코드 리뷰 이후 [Review changes]를 클릭하면 [Write]창이 열리는데 댓글만 달고 싶다면 [Comment]를, 댓글을 달고 코드가 좋아 바로 병합해도 될 것 같으면 [Approve]을, 수정을 요청하고 싶으면 [Request changes]를 선택한다. 일단 [Approve]를 선택하자.
> 
> 4. 코드 리뷰도 마치고 승인까지 했으니 이제 병합을 해도 될 것 같다. [Merge pull request]버튼을 눌러 풀 리퀘스트를 병합한다. 이것은 원본저장소 주인만 할 수 있다.
> 
> 5. 병합이 성공적으로 완료됐으면 '### merge commit' 메시지가 뜬다.
> 
> 6. 원본저장소에 원격저장소 코드가 병합되었다. [Code]탭을 클릭하면 'like.md' 파일이 원본저장소에 잘 들어간 것을 확인할 수 있다.
> 
> 7. [Insights] 탭의 [Contributors] 메뉴에 가보면 이제 원본저장소의 컨트리뷰터에 포함된 것을 확인할 수 있다.
> 
> 8. 오픈소스에 기여를 한 뒤 프로필 페이지에서 [Customize your pins] 텍스트를 클릭하여 첫 페이지에 노출되는 원본저장소 목록을 지정할 수 있다.

## 4-3. 묵은 커밋을 새 커밋으로 이력 조작하기(rebase)

### 4-3-1. 원본저장소에 새로운 커밋이 있는데, 포크한 내 원격저장소에는 안 보여요!

* 원본저장소에서 두 개의 커밋을 한 것을 원격 저장소에서 모르고 풀 리퀘스트를 했다는 상황 가정

### 4-3-2. 여러 원격저장소 히스토리를 한 눈에 보기: 리모트 추가(Add remote)

* 포크한 시점까지는 원격저장소가 알 수 있지만, 그 이후로는 무슨 일이 일어났는지 알 수 없습니다. 그렇다면 내 원격저장소에서 다른 원본저장소의 히스토리도 함께 보고 싶다면 어떻게 하면 될까요?

> 1. 소스트리 원격저장소 탭으로 이동해 [저장소 - 원격 저장소 추가]를 클릭합니다.
> 2. 새로 추적하고 싶은 저장소를 추가합니다(이번 상황에서는 원본저장소를 추가합니다).
> 3. 원격 이름은 자유롭게 적어도 되나, 이번 경우에는 upstream으로 짓겠습니다.
> 4. upstream에서 가져오기를 클릭하여 원본저장소에 있는 커밋 히스토리를 받아옵니다. 이것을 페치(Fetch)라고 합니다.
> 5. 페치는 간단히 말하면 새로고침 기능으로, 원본저장소 이력을 업데이트합니다. 예를 들어 동료 개발자가 [master] 브랜치에 커밋을 5개 올렸는데 내 소스트리에는 아직 그 이력이 안 보일 때 패치를 하면 이력이 보입니다. 풀은 최신 코드를 내 코드에 반영하는 것이기 때문에 페치와 풀은 다릅니다.

### 4-3-3. 묵은 커밋을 방금 한 커밋처럼: 리베이스(Rebase)

* 풀 리퀘스트를 보냈을 때 충돌이 난다면 두 가지 방법을 택할 수 있습니다. 첫 번째는 현재 커밋과 병합하고 싶은 커밋을 미리 내 브랜치에서 병합 커밋을 만들고 이를 풀 리퀘스트로 보내는 방법입니다.

* 충돌이 발생하는 부분을 해결하고 만든 병합 커밋을 올리면 충돌이 나지는 않지만, 풀 리퀘스트에서 불필요한 커밋의 이력이 생기게 됩니다. 이를 위해서 묵은 커밋을 방금 한 커밋처럼 이력을 조작하는 것입니다.

* 원본저장소의 옛 커밋을 base로 원격저장소가 커밋을 진행하였고, 원본저장소는 base에서 커밋을 또 올렸을 때, 커밋의 베이스를 원본저장소의 새 커밋으로 옮기면 빨리감기 머지가 가능한 상태일 것입니다.

* 이렇게 커밋의 베이스를 떼어내 다른 곳으로 붙이는 것이 리베이스(rebase)입니다. 예전에 커밋을 기준으로 만들었던 브랜치를, 최신 코드를 기준으로 만든 것처럼 조작하는 것입니다.

> 소스트리에서 재배치를 누른 후 충돌이 난 부분을 수정한 이후 재배치를 계속하여 리베이스 한다. 이때, 푸시를 하게 되면 히스토리를 강제로 조작하는 것이기 때문에 다른 개발자가 이 변경 사항을 사용하지 있지 않아야 한다.

# Chapter 5. 실무 사례와 함께 Git 배우기

## 5-1. 실습을 위한 사전 준비: 새로운 원격저장소 만들기

* GitHub에서 New repository를 만들고 소스트리에서 클론

## 5-2. amend: 수정 못한 파일이 있어요, 방금 만든 커밋에 추가하고 싶어요.

### 5-2-1. amend로 마지막 커밋 수정하기

* 파일을 생성하여 커밋을 한 이후, 파일의 수정을 깜빡하여 다시 수정을 하고 재커밋을 올리는 것 보다 커밋을 수정하는 편이 더 깔끔할 것입니다.

* 소스트리에서 수정 사항을 스테이지에 올리고 커밋 옵션에서 마지막 커밋 정정 옵션을 선택한 채 커밋을 올리면 됩니다.

### 5-2-2. amend로 마지막 커밋 메시지를 수정하고 원격저장소 브랜치에 강제 푸시하기

* 소스트리에서 마지막 커밋 정정으로 다시 커밋을 수정하고, 푸시할 때는 [강제 푸시]로 로컬저장소의 변경사항을 원격저장소에 강제로 덮어씌웁니다.

## 5-3. cherry-pick: 저 커밋 하나만 떼서 지금 브랜치에 붙이고 싶어요.

### 5-3-1. cherry-pick: 다른 브랜치의 커밋 하나만 내 브랜치에 반영하기

* 다른 브랜치에서 내 브랜치로 추가하면 좋을 커밋을 받기 위해 병합할 필요 없이 다른 브랜치의 커밋을 체리픽하여 내 브랜치의 최신 커밋으로 불러올 수 있습니다.

## 5-4. reset: 옛날 커밋으로 브랜치를 되돌리고 싶어요

### 5-4-1. Soft/Mixed reset: 모든 기억을 남기면서 브랜치를 되돌리기

* 원하는 시점의 커밋에 마우스 우클릭하여 [이 커밋까지 현재 브랜치를 초기화]를 선택합니다. 모드는 [Soft], [Mixed], [Hard] 모드 중 하나를 선택해야 합니다.

* Soft 모드는 변경사항을 커밋하기 전 상태로 되돌리며, 변경 사항을 스테이지 위로 둬서 다시 당장 커밋할 수 있고, Mixed모드는 스테이지 아래로 두어서 어떤 것을 다시 스테이지 위로 Add 할지 선택할 수 있습니다.

### 5-4-2. Hard reset: 모든 기억을 지우며 브랜치를 되돌리기

* Hard 모드는 이전의 커밋은 모두 지우는 것입니다. 원격브랜치에도 적용하기 위해서는 히스토리를 조작하는 것이기 때문에 강제푸시로 푸시해줍니다.

## 5-5. revert: 이 커밋의 변경사항을 되돌리고 싶어요

* 변경사항을 되돌리기 위해 되돌리고 싶은 커밋에서 [커밋 되돌리기]를 선택합니다.

## 5-6. stash: 변경 사항을 잠시 다른 곳에 저장하고 싶어요, 커밋은 안 만들래요

현재 브랜치에서 개발하고 있는데 급히 고쳐야 하는 버그가 발생했습니다. 그런데 현재 브랜치에는 아직 커밋하지 않은 변경사항이 있습니다. 하지만 커밋하기에는 애매한 파일들입니다. 이때 이 변경사항을 잠시 보관해두었다가 다시 사용하는 것이 스태시(stash)입니다.