```
본 문서는 한빛미디어, 우재남님의
'혼자 공부하는 SQL'
을 참고하여 정리한 문서입니다.
```

- [Chapter 1. 데이터베이스와 SQL](#chapter-1-데이터베이스와-sql)
  - [1-1. 데이터베이스 알아보기](#1-1-데이터베이스-알아보기)
    - [1-1-1. 데이터베이스와 DBMS](#1-1-1-데이터베이스와-dbms)
      - [DMBS의 정의](#dmbs의-정의)
      - [DBMS의 종류](#dbms의-종류)
    - [1-1-2. DBMS의 발전과정](#1-1-2-dbms의-발전과정)
      - [종이에 펜으로 기록](#종이에-펜으로-기록)
      - [컴퓨터에 파일로 저장](#컴퓨터에-파일로-저장)
      - [DBMS의 대두와 보급](#dbms의-대두와-보급)
    - [1-1-3. DBMS의 종류](#1-1-3-dbms의-종류)
      - [계층형 DBMS](#계층형-dbms)
      - [망형 DBMS](#망형-dbms)
      - [관계형 DBMS](#관계형-dbms)
    - [1-1-4. DBMS에서 사용되는 언어: SQL](#1-1-4-dbms에서-사용되는-언어-sql)
- [Chapter 2. 실전용 SQL 미리 맛보기](#chapter-2-실전용-sql-미리-맛보기)
  - [2-1. 건물을 짓기 위한 설계도: 데이터베이스 모델링](#2-1-건물을-짓기-위한-설계도-데이터베이스-모델링)
    - [2-1-1. 프로젝트 진행 단계](#2-1-1-프로젝트-진행-단계)
    - [2-1-2. 데이터베이스 모델링](#2-1-2-데이터베이스-모델링)
    - [2-1-3. 전체 데이터베이스 구성도](#2-1-3-전체-데이터베이스-구성도)
  - [2-2. 데이터베이스 시작부터 끝까지](#2-2-데이터베이스-시작부터-끝까지)
    - [2-2-1. DBMS 설치하기](#2-2-1-dbms-설치하기)
    - [2-2-2. 데이터베이스 만들기](#2-2-2-데이터베이스-만들기)
    - [2-2-3. 테이블 만들기](#2-2-3-테이블-만들기)
      - [테이블 설계하기](#테이블-설계하기)
      - [테이블 생성하기](#테이블-생성하기)
    - [2-2-4. 데이터 입력하기](#2-2-4-데이터-입력하기)
    - [2-2-5. 데이터 활용하기](#2-2-5-데이터-활용하기)
  - [2-3. 데이터베이스 개체](#2-3-데이터베이스-개체)
    - [2-3-1. 인덱스](#2-3-1-인덱스)
      - [인덱스 개념 이해하기](#인덱스-개념-이해하기)
      - [인덱스 실습하기](#인덱스-실습하기)
    - [2-3-2. 뷰](#2-3-2-뷰)
      - [뷰 개념 이해하기](#뷰-개념-이해하기)
      - [뷰 실습하기](#뷰-실습하기)
    - [2-3-3. 스토어드 프로시저](#2-3-3-스토어드-프로시저)
      - [스토어드 프로시저 개념 이해하기](#스토어드-프로시저-개념-이해하기)
      - [스토어드 프로시저 실습하기](#스토어드-프로시저-실습하기)
    - [2-3-4. CREATE 문과 DROP 문](#2-3-4-create-문과-drop-문)
- [Chapter 3. SQL 기본 문법](#chapter-3-sql-기본-문법)
  - [3-1. 기본 중에 기본 SELECT ~ FROM ~ WHERE](#3-1-기본-중에-기본-select--from--where)
    - [3-1-1. 실습용 데이터베이스 구축](#3-1-1-실습용-데이터베이스-구축)
      - [실습용 데이터베이스 개요](#실습용-데이터베이스-개요)
      - [market_db.sql 파일 내용 살펴보기](#market_dbsql-파일-내용-살펴보기)
    - [3-1-2. 기본 조회하기: SELECT ~ FROM](#3-1-2-기본-조회하기-select--from)
      - [USE문](#use문)
      - [SELECT 문의 기본 형식](#select-문의-기본-형식)
      - [SELECT와 FROM](#select와-from)
    - [3-1-3. 특정한 조건만 조회하기: SELECT ~ FROM ~ WHERE](#3-1-3-특정한-조건만-조회하기-select--from--where)
      - [WHERE 없이 조회하기](#where-없이-조회하기)
      - [기본적인 WHERE 절](#기본적인-where-절)
      - [관계 연산자, 논리 연산자의 사용](#관계-연산자-논리-연산자의-사용)
      - [BETWEEN ~ AND](#between--and)
      - [IN()](#in)
      - [LIKE](#like)
    - [3-1-4. 서브 쿼리](#3-1-4-서브-쿼리)
  - [3-2. 좀 더 깊게 알아보는 SELECT문](#3-2-좀-더-깊게-알아보는-select문)
    - [3-2-1. ORDER BY 절](#3-2-1-order-by-절)
      - [출력의 개수를 제한: LIMIT](#출력의-개수를-제한-limit)
      - [중복된 결과를 제거: DISTINCT](#중복된-결과를-제거-distinct)
    - [3-2-2. GROUP BY 절](#3-2-2-group-by-절)
      - [집계 함수](#집계-함수)
      - [HAVING 절](#having-절)
  - [3-3. 데이터 변경을 위한 SQL문](#3-3-데이터-변경을-위한-sql문)
    - [3-3-1. 데이터 입력: INSERT](#3-3-1-데이터-입력-insert)
      - [INSERT 문의 기본 문법](#insert-문의-기본-문법)
      - [자동으로 증가하는 AUTO_INCREMENT](#자동으로-증가하는-auto_increment)
      - [다른 테이블의 데이터를 한 번에 입력하는 INSERT INTO ~ SELECT](#다른-테이블의-데이터를-한-번에-입력하는-insert-into--select)
    - [3-3-2. 데이터 수정: UPDATE](#3-3-2-데이터-수정-update)
      - [UPDATE 문의 기본 문법](#update-문의-기본-문법)
      - [WHERE가 없는 UPDATE문](#where가-없는-update문)
  - [3-3-3. 데이터 삭제: DELETE](#3-3-3-데이터-삭제-delete)
  - [3-3-4. 대용량 테이블의 삭제](#3-3-4-대용량-테이블의-삭제)
- [Chapter 4. SQL 고급 문법](#chapter-4-sql-고급-문법)
  - [4-1. MySQL의 데이터 형식](#4-1-mysql의-데이터-형식)
    - [4-1-1. 데이터 형식](#4-1-1-데이터-형식)
      - [정수형](#정수형)
      - [문자형](#문자형)
      - [대량의 데이터 형식](#대량의-데이터-형식)
      - [실수형](#실수형)
      - [날짜형](#날짜형)
    - [4-1-2. 변수의 사용](#4-1-2-변수의-사용)
    - [4-1-3. 데이터 형 변환](#4-1-3-데이터-형-변환)
      - [함수를 이용한 명시적인 변환](#함수를-이용한-명시적인-변환)
      - [암시적인 변환](#암시적인-변환)
  - [4-2. 두 테이블을 묶는 조인](#4-2-두-테이블을-묶는-조인)
    - [4-2-1. 내부 조인](#4-2-1-내부-조인)
      - [일대다 관계의 이해](#일대다-관계의-이해)
      - [내부 조인의 기본](#내부-조인의-기본)
      - [내부 조인의 간결한 표현](#내부-조인의-간결한-표현)
      - [내부 조인의 활용](#내부-조인의-활용)
      - [중복된 결과 1개만 출력하기](#중복된-결과-1개만-출력하기)
    - [4-2-2. 외부 조인](#4-2-2-외부-조인)
      - [외부 조인의 기본](#외부-조인의-기본)
      - [외부 조인의 활용](#외부-조인의-활용)
    - [4-2-3. 기타 조인](#4-2-3-기타-조인)
      - [상호 조인](#상호-조인)
      - [자체 조인](#자체-조인)
  - [4-3. SQL 프로그래밍](#4-3-sql-프로그래밍)
    - [4-3-1. IF문](#4-3-1-if문)
      - [IF문의 기본 형식](#if문의-기본-형식)
      - [IF ~ ELSE 문](#if--else-문)
      - [IF 문의 활용](#if-문의-활용)
    - [4-3-2. CASE 문](#4-3-2-case-문)
      - [CASE 문의 기본 형식](#case-문의-기본-형식)
      - [CASE 문의 활용](#case-문의-활용)
    - [4-3-3. WHILE 문](#4-3-3-while-문)
      - [WHILE 문의 기본 형식](#while-문의-기본-형식)
      - [WHILE 문의 응용](#while-문의-응용)
    - [4-3-4. 동적 SQL](#4-3-4-동적-sql)
      - [PREPARE와 EXECUTE](#prepare와-execute)
      - [동적 SQL의 활용](#동적-sql의-활용)
- [Chapter 5. 테이블과 뷰](#chapter-5-테이블과-뷰)
  - [5-1. 테이블 만들기](#5-1-테이블-만들기)
    - [5-1-1. 데이터베이스와 테이블 설계하기](#5-1-1-데이터베이스와-테이블-설계하기)
    - [5-1-2. GUI 환경에서 테이블 만들기](#5-1-2-gui-환경에서-테이블-만들기)
      - [데이터 베이스 생성하기](#데이터-베이스-생성하기)
      - [테이블 생성하기](#테이블-생성하기-1)
      - [데이터 입력하기](#데이터-입력하기)
    - [5-1-3. SQL로 테이블 만들기](#5-1-3-sql로-테이블-만들기)
      - [데이터베이스 생성하기](#데이터베이스-생성하기)
      - [테이블 생성하기](#테이블-생성하기-2)
      - [데이터 입력하기](#데이터-입력하기-1)
  - [5-2. 제약조건으로 테이블을 견고하게](#5-2-제약조건으로-테이블을-견고하게)
    - [5-2-1. 제약조건의 기본 개념과 종류](#5-2-1-제약조건의-기본-개념과-종류)
    - [5-2-2. 기본 키 제약조건](#5-2-2-기본-키-제약조건)
      - [CREATE TABLE에서 설정하는 기본 키 제약조건](#create-table에서-설정하는-기본-키-제약조건)
      - [ALTER TABLE에서 설정하는 기본 키 제약조건](#alter-table에서-설정하는-기본-키-제약조건)
    - [5-2-3. 외래 키 제약조건](#5-2-3-외래-키-제약조건)
      - [CREATE TABLE에서 설정하는 외래 키 제약조건](#create-table에서-설정하는-외래-키-제약조건)
      - [ALTER TABLE에서 설정하는 외래 키 제약조건](#alter-table에서-설정하는-외래-키-제약조건)
      - [기준 테이블의 열이 변경될 경우](#기준-테이블의-열이-변경될-경우)
    - [5-2-4. 기타 제약조건](#5-2-4-기타-제약조건)
      - [고유 키 제약조건](#고유-키-제약조건)
      - [체크 제약조건](#체크-제약조건)
      - [기본값 정의](#기본값-정의)
      - [NULL 값 허용](#null-값-허용)

# Chapter 1. 데이터베이스와 SQL

## 1-1. 데이터베이스 알아보기

* 데이터베이스에는 우리 일상생활 대부분의 정보가 저장되고 관리됩니다.

* **데이터베이스(Database, DB)** 를 한 마디로 정의한다면 '데이터의 집합'이라고 할 수 있습니다.

### 1-1-1. 데이터베이스와 DBMS

#### DMBS의 정의

* 데이터베이스를 관리하고 운영하는 소프트웨어를 **DBMS(Database Management System)** 라고 합니다. 다양한 데이터가 저장되어 있는 데이터베이스는 여러 명의 사용자나 응용 프로그램과 공유하고 동시에 접근이 가능해야 합니다.

* 엑셀과 같은 프로그램은 '데이터의 집합'을 관리하고 운영한다는 차원에서는 DBMS라고 볼 수 있지만, *대용량의 데이터를 관리하거나 여러 사용자와 공유하는 개념과는 거리가 있어 DBMS라고 부르지 않습니다.*

#### DBMS의 종류

* DBMS는 대표적으로 MySQL, 오라클(Oracle), SQL 서버(Server), MariaDB 등이 있습니다.

### 1-1-2. DBMS의 발전과정

#### 종이에 펜으로 기록

#### 컴퓨터에 파일로 저장

* 컴퓨터가 등장한 이후 프로그램을 통해 더욱 효율적으로 정보를 관리하게 되었습니다. 기록된 내용은 파일(file)이라는 형태로 저장해 필요할 때마다 열어서 사용할 수 있습니다.

#### DBMS의 대두와 보급

* 앞서 파일은 여러 명의 사람들이 이용하기에 불용이하였기에 이를 보완하며 대량의 데이터를 효율적으로 관리하고 운영하기 위해서 등장한 것이 DBMS입니다.

* DBMS는 데이터의 집합인 데이터베이스를 잘 관리하고 운영하기 위한 시스템 또는 소프트웨어를 말합니다. DBMS에 데이터를 구축, 관리하고 활용하기 위해서 사용되는 언어가 **SQL(Structured Query Language)** 입니다.

* 즉, SQL문을 잘 이해하고 사용해야만 DBMS를 원활하게 활용할 수 있습니다. 

### 1-1-3. DBMS의 종류

#### 계층형 DBMS

* 계층형 DBMS(Hierarchical DBMS)는 처음으로 등장한 DBMS 개념으로 각 계층은 트리(tree) 형태를 갖습니다.
* 계층형 DBMS의 문제는 처음 구성을 완료한 후에 이를 변경하기가 상당히 까다롭다는 것입니다. 회사 내 수직적인 구조처럼 여러 단계를 거쳐야 합니다. 지금은 사용하지 않는 형태입니다.

#### 망형 DBMS

* 망형 DBMS(Network DBMS)는 계층형 DBMS의 문제점을 개선하기 위해 등장했으며, 하위에 있는 구성원끼리도 연결된 유연한 구조입니다.
* 망형 DBMS를 잘 활용하려면 프로그래머가 모든 구조를 이해해야만 프로그램 작성이 가능하다는 단점이 존재합니다. 역시 지금은 거의 사용하지 않는 형태입니다.

#### 관계형 DBMS

* 관계형 DBMS(Relational DBMS)는 줄여서 **RDBMS**라고 부릅니다. 우리가 사용할 MySQL뿐만 아니라 대부분의 DBMS가 RDBMS 형태로 사용됩니다. RDBMS의 데이터베이스는 테이블(table)이라는 최소 단위로 구성되며, 이 테이블은 하나 이상의 열(column)과 행(row)으로 이루어져 있습니다.
* 테이블은 열과 행으로 이루어진 2차원 구조를 갖습니다. 세로는 열, 가로는 행이라고 합니다.

>![테이블-출처: 위키피디아](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7c/Relational_database_terms.svg/525px-Relational_database_terms.svg.png)  
> 출처: 위키피디아

### 1-1-4. DBMS에서 사용되는 언어: SQL

* SQL은 관계형 데이터베이스에서 사용되는 언어로 관계형 DBMS를 배우려면 필수로 익혀야 합니다.

* SQL은 국제표준화기구에서 SQL에 대한 표준을 정해서 발표하고 있습니다. 이를 **표준 SQL**이라고 합니다. DBMS를 만드는 회사에서는 되도록 표준 SQL을 준수하되, 각 제품의 특성을 반영한 SQL을 사용합니다. 

# Chapter 2. 실전용 SQL 미리 맛보기

## 2-1. 건물을 짓기 위한 설계도: 데이터베이스 모델링

* **데이터베이스 모델링(database modeling)** 은 테이블의 구조를 미리 설계하는 개념으로 프로젝트에서 데이터베이스 모델링이 잘 되어야 제대로 된 데이터베이스를 구축할 수 있습니다.

* 프로젝트를 진행하기 위해서는 대표적으로 **폭포수 모델(waterfall model)** 을 사용하여, 데이터베이스 모델링은 폭포수 모델의 업무 분석과 시스템 설계 단계에 해당합니다. 이 단계를 거치면 가장 중요한 데이터베이스 개체인 **테이블 구조**가 결정되는 것입니다.

### 2-1-1. 프로젝트 진행 단계

* 프로젝트란 '현실 세계에서 일어나는 업무를 컴퓨터 시스템으로 옮겨놓는 과정'입니다. 더 쉽게는 '대규모 소프트웨어를 작성하기 위한 전체 과정'이라고 이야기할 수 있습니다.

* 소프트웨어 개발 절차 중 하나로 **폭포수 모델(waterfall model)** 이라는 것이 있습니다.

> 슈퍼마켓의 물건을 판매하기 위한 프로젝트 진행
> 1. 프로젝트 계획: 슈퍼마켓의 물건들을 온라인으로 판매하기 위한 계획 단계입니다.  
>   
> 2. 업무 분석: 슈퍼마켓에서 업무가 어떻게 돌아가는지 파악하는 것입니다. 예로 물건은 어디서 들어오는지, 물건을 어떻게 계산하는지, 재고는 어떻게 관리하는지 등의 업무에 대해서 정리하는 단계입니다.
> 
> 3. 시스템 설계: 앞에서 정리한 업무 분석을 컴퓨터에 적용시키기 위해서 알맞은 형태로 다듬는 과정입니다.
> 
> 4. 프로그램 구현: 앞에서 완성한 시스템 설계의 결과를 실제 프로그래밍 언어로 코딩하는 단계입니다. 우리가 계획한 내용을 온라인으로 제공하기 위해서는 JavaScript, PHP, JSP 등의 프로그래밍 언어를 사용해야 합니다.
> 
> 5. 테스트: 코딩된 프로그램에 오류가 없는지 확인하는 과정입니다.
> 
> 6. 유지보수: 실제 온라인 쇼핑몰을 운영하면서 문제점을 보완하고 기능을 추가하는 과정입니다.

* 우리가 공부하는 데이터베이스 모델링은 폭포수 모델에서 업무 분석과 시스템 설계 단계에 해당합니다. 8장에서 프로그램 구현과 데이터베이스 연결도 실제로 구현해보겠습니다.

### 2-1-2. 데이터베이스 모델링

* 데이터베이스 모델링이란 우리가 살고 있는 세상에서 사용되는 사물이나 작업을 DBMS의 데이터베이스 개체로 옮기기 위한 과정이라고 할 수 있습니다.

* 우리가 구현할 인터넷 쇼핑몰에서는 고객 또는 직원 등의 사람이 필요합니다. 사람을 나타낼 수 있는 특징들을 추출해서 데이터베이스로 만들어야 합니다. 슈퍼마켓(현실 세계)의 고객, 물건, 직원 등을 데이터베이스에 각각의 **테이블**이라는 개체로 변환합니다.

* 예: 신분증에 이름, 주민등록번호, 주소 등의 정보가 있는 것

### 2-1-3. 전체 데이터베이스 구성도

![데이터베이스 구성도](img%201-1.jpg)  
(직접 제작)  

* 데이터: 하나하나의 단편적인 정보를 말합니다. 테이블에 들어가는 각각의 정보를 의미합니다.

* 테이블: 데이터를 입력하기 위해 표 형태로 표현한 것을 말합니다.

* 데이터베이스: 테이블이 저장되는 저장소를 말합니다. 각 데이터베이스는 이름이 서로 달라야 합니다.

* DBMS: 데이터베이스 관리 시스템 또는 소프트웨어를 말합니다.

* 열: 테이블의 세로를 말합니다.

* 열 이름: 각 열을 구분하기 위한 이름입니다. 열 이름은 각 테이블 내에서는 서로 달라야 합니다.

* 데이터 형식: 열에 저장될 데이터의 형식을 말합니다. 데이터 형식은 테이블을 생성할 때 열 이름과 함께 지정해줍니다.

* 행: 실질적인 진짜 데이터를 말합니다. 각각 속한 데이터를 행 데이터라고 부릅니다. 즉, 행의 개수가 데이터의 개수입니다.

* 기본 키(Primary Key, PK): 기본 키 열은 각 행을 구분하는 유일한 열을 말합니다. 가장 중요한 혹은 기초적인 열이며, 기본키는 중복되어서는 안 되며, 비어 있어서도 안됩니다.

* SQL: DBMS에서 작업을 하고 싶다면 DBMS가 알아듣는 언어(말)로 해야 합니다. 그것이 SQL(구조화된 질의 언어)입니다. 즉, SQL은 사람과 DBMS가 소통하기 위한 언어입니다.

## 2-2. 데이터베이스 시작부터 끝까지

* 데이터베이스는 데이터를 저장하는 공간입니다. MySQL을 설치한 후에는 가장 먼저 데이터베이스를 준비해야 합니다. 그리고 데이터베이스 안에 테이블을 생성해야 합니다.

* 테이블은 2차원의 표 형태로 이루어져 있으며, 각 열에 해당하는 데이터를 한 행씩 입력할 수 있습니다. 필요하다면 행에 입력된 데이터를 수정하거나 삭제할 수도 있습니다. 마지막으로 입력이 완료된 데이터를 조회해서 활용할 수 있습니다.

### 2-2-1. DBMS 설치하기

### 2-2-2. 데이터베이스 만들기

1. [SCHEMAS] 패널의 빈 부분에서 마우스 오른쪽 버튼을 클릭한 후 [Create Schema]를 선택합니다.

2. 새로운 쿼리창에서 [Name]을 입력 후 [Apply]버튼을 클릭하면 SQL문이 자동으로 생성됩니다.

### 2-2-3. 테이블 만들기

#### 테이블 설계하기

* 테이블을 설계하기 위해서 테이블의 열 이름과 데이터 형식을 지정해야 합니다.

* 문자는 CHAR(Character)라는 예약어를 사용해야 합니다,

* 널(Null)은 빈 것을 의미하며 널 허용 안 함(Not Null, NN)은 반드시 입력해야 한다는 의미입니다.

* INT는 Integer의 약자로 정수를 의미하며 DATE는 연, 월, 일을 입력합니다.

#### 테이블 생성하기

1. 데이터베이스를 클릭해 Tables를 마우스 우클릭한 후 Create Table을 선택합니다.

2. 테이블 이름에 'member'(예시) 입력하고 Column Name의 첫 번째 항목을 더블 클릭합니다.

3. 열 이름은 'member_id'로 입력하고 데이터 형식은 문자 8글자이므로 'CHAR(8)'이라고 입력합니다. 그리고 설계할 때 아이디(member_id)열을 기본 키로 설정하기로 했으므로 PK와 NN을 체크합니다.

4. 이어서 나머지 테이블을 설계한 후 apply 버튼을 클릭합니다.

### 2-2-4. 데이터 입력하기

1. MySQL Workbench 창의 SCHEMAS 패널에서 member 테이블을 선택하고 마우스 오른쪽 버튼을 클릭한 후 [Select Rows - Limits 1000]을 선택합니다.

2. Result Grid 창에서 NULL 부분을 클릭해서 데이터를 입력한 후 Apply 버튼을 클릭하면 입력한 내용이 SQL로 생성됩니다.

**기본 키로 설정한 열이 기준이 되어 오름차순으로 자동 정렬됩니다.**

3. 값을 수정할 때는 UPDATE 문이 생성되며, 데이터를 삭제할 때는 DELETE문이 생성됩니다.

### 2-2-5. 데이터 활용하기

* SQL에서는 데이터베이스를 활용하기 위해 주로 SELECT 문을 사용합니다.

1. 쿼리 창이 열려 있지 않은 상태에서 새 SQL을 입력하기 위해 툴 바의 Create a new SQL tab for executing queries 아이콘을 클릭합니다. 실행된 결과를 확인하기 위해 Output 아이콘을 클릭하여 Output 패널도 활성화합니다.

2. 작업할 데이터베이스를 선택하기 위해 SCHEMAS 패널의 'shop_db'를 더블 클릭합니다.

3. 먼저 회원 테이블의 모든 행을 조회하기 위해 다음 SQL을 입력합니다. SELECT의 기본 형식은 SELECT 열_이름 FROM 테이블_이름 [WHERE 조건]이고, *는 모든 열을 의미합니다. 툴바에서 Execute the selected portion of the script or everything 아이콘을 클릭하면 Result Grid 창에는 결과가, Output 패널에는 현재 결과의 건수와 조회하는데 소요된 시간(초)이 표시됩니다.

**SQL의 제일 뒤에는 세미콜론(;)이 꼭 있어야 합니다.**

4. 회원 테이블 중 이름과 주소만 출력해보겠습니다.

> 
>  ```SQL
>  SELECT member_name, member_addr FROM member;
>  ```
> 이렇게 여러 개의 열 이름을 콤마(,)로 분리하면 필요한 열만 추출됩니다.

5. 아이유 회원에 대한 정보만 추출해보겠습니다. WHERE 다음에 특정 조건을 입력하여 회원 이름(member_name)이 '아이유'인 회원만 출력되도록 한 것입니다.

> 
> ```SQL
> SELECT * FROM member WHERE member_name = '아이유';
> ```

## 2-3. 데이터베이스 개체

* 테이블은 데이터베이스의 핵심 개체이지만, 그외에도 **인덱스, 뷰, 스토어드 프로시저**, 트리거, 함수, 커서 등의 개체도 필요합니다.

* 인덱스는 데이터를 조회할 때 결과가 나오는 속도를 획기적으로 빠르게 해주고, 뷰는 테이블의 일부를 제한적으로 표현할 때 주로 사용합니다. 스토어드 프로시저는 SQL에서 프로그래밍이 가능하도록 해주고, 트리거는 잘못된 데이터가 들어가는 것을 미연에 방지하는 기능을 합니다.

* 모든 데이터베이스 개체는 테이블과 상호 연관이 있습니다.

### 2-3-1. 인덱스

* 데이터를 조회할 때 테이블에 데이터가 많아질수록 결과가 나오는 시간이 많이 소요됩니다. 인덱스는 이런 경우 결과가 나오는 시간을 대폭 줄여줍니다.

#### 인덱스 개념 이해하기
  
* 인덱스란 책의 찾아보기와 비슷합니다. 찾아보기를 통해 원하는 단어를 찾아 그 페이지로 이동하는 효율적인 방법입니다.

* 실무에서는 수천만~수억 건 이상의 데이터를 처리할 때 인덱스 없이 전체 데이터를 찾을 수 없습니다.

#### 인덱스 실습하기

```SQL
CREATE INDEX idx_member_name ON member(member_name);
```

* 위 SQL 문장에서 `ON member(member_name);`의 의미는 member 테이블의 member_name 열에 인덱스를 지정하라는 의미입니다. 이를 통해 인덱스를 생성할 수 있습니다.

* 인덱스를 생성한 후 다시 SELECT문을 실행하면 **Non-Unique Key Lookup**으로 결과를 찾았다고 나오는데, Key Lookup은 인덱스를 통해 결과를 찾았다고 기억하면 됩니다. 이런 방법은 **인덱스 검색(Index Scan)** 이라고 부릅니다

### 2-3-2. 뷰

* 뷰를 활용하면 보안도 강화하고, SQL 문도 간단하게 사용할 수 있습니다.

#### 뷰 개념 이해하기

* 뷰(view)를 한 마디로 정의하면 '가상의 테이블'이라고 할 수 있습니다. 일반 사용자의 입장에서는 테이블과 뷰를 구분할 수 없습니다. 다만 뷰는 실제 데이터를 가지고 있지 않으며, 진짜 테이블에 링크(link)된 개념이라고 생각하면 됩니다.

* 윈도우즈의 '바로 가기 아이콘'과 같이 실제로 저장된 프로그램 파일과 아이콘을 연결해주는 맥락과 비슷합니다.

* 뷰는 실체는 없으며 테이블과 연결되어 있는 것뿐입니다. 뷰의 실체는 바로 SELECT문입니다.

#### 뷰 실습하기

```SQL
CREATE VIEW member_view
AS
    SELECT * FROM member;
```

* 위와 같은 식을 통해 VIEW를 생성할 수 있고, 이렇게 만들어놓은 뷰를 통해 정보를 확인할 수 있습니다.

```SQL
SELECT * FROM member_view;
```

* 뷰를 사용하는 이유는 **보안에 도움이 되며, 긴 SQL 문을 간략하게 만들 수 있기 때문입니다.**

### 2-3-3. 스토어드 프로시저

#### 스토어드 프로시저 개념 이해하기

* 스토어드 프로시저란 MySQL에서 제공하는 **프로그래밍 기능**으로, 여러 개의 SQL문을 하나로 묶어서 편리하게 사용할 수 있습니다.

#### 스토어드 프로시저 실습하기  

> 1. 자주 반복해서 사용할 SQL문이 있다고 할 때, 매번 SQL문을 입력하면 오타를 입력할 수도 있으며 시간이 오래 소요될 수 있습니다. 따라서 이러한 SQL문을 스토어드 프로시저로 만들어서 사용하는 것이 더 효율적일 것입니다.
> 
> 2.
> ```SQL
> DELIMITER //
> CREATE PROCEDURE myProc()
> BEGIN
>   	SELECT * FROM member WHERE member_name = '나훈아';
>     SELECT * FROM product WHERE product_name = '삼각김밥';
> END //
> DELIMITER;
> ```
> 
> * 첫 행과 마지막 행에 **구분 문자**라는 의미의 **`DELIMITER // ~ DELIMITER ;`** 문이 나왔습니다. 이것은 스토어드 프리시저를 묶어주는 약속이라고 생각합니다. 그리고 **BEGIN과 END** 사이에 SQL 문을 넣으면 됩니다.
> 
> 3. 이제부터 BEGIN과 END 사이의 SQL문을 실행할 필요 없이 만들어둔 스토어드 프로시저를 호출하기 위해서 CALL문을 실행하면 됩니다.
> 
> ```SQL
> CALL myProc()
> ```


### 2-3-4. CREATE 문과 DROP 문

* 데이터베이스 개체를 만들기 위해 `CREATE 개체_종류 개체_이름 ~`의 형식을 사용합니다.

* 이와 반대로 데이터베이스 개체를 삭제하기 위해서는 `DROP 개체_종류 개체_이름` 형식을 사용합니다.

# Chapter 3. SQL 기본 문법

## 3-1. 기본 중에 기본 SELECT ~ FROM ~ WHERE

* SELECT 문은 구축이 완료된 테이블에서 데이터를 추출하는 기능을 합니다. 그러므로 SELECT를 아무리 많이 사용해도 기존의 데이터가 변경되지는 않습니다.

* SELECT의 가장 기본 형식은 `SELECT ~ FROM ~ WHERE`입니다. SELECT 바로 다음에는 **열 이름**이, FROM 다음에는 **테이블 이름**이 나옵니다. WHERE 다음에는 **조건식**이 나오는데, 조건식을 다양하게 표현함으로써 데이터베이스에서 원하는 데이터를 추출할 수 있습니다.

### 3-1-1. 실습용 데이터베이스 구축

#### 실습용 데이터베이스 개요

* '인터넷 마켓 DB 구상도' 파일을 통해 실습 데이터를 구축.
* 생략

#### market_db.sql 파일 내용 살펴보기

```sql
DROP DATABASE IF EXISTS market_db; -- 만약 market_db가 존재하면 우선 삭제한다.
CREATE DATABASE market_db;

USE market_db;
CREATE TABLE member -- 회원 테이블
( mem_id  		CHAR(8) NOT NULL PRIMARY KEY, -- 사용자 아이디(PK)
  mem_name    	VARCHAR(10) NOT NULL, -- 이름
  mem_number    INT NOT NULL,  -- 인원수
  addr	  		CHAR(2) NOT NULL, -- 지역(경기,서울,경남 식으로 2글자만입력)
  phone1		CHAR(3), -- 연락처의 국번(02, 031, 055 등)
  phone2		CHAR(8), -- 연락처의 나머지 전화번호(하이픈제외)
  height    	SMALLINT,  -- 평균 키
  debut_date	DATE  -- 데뷔 일자
);
CREATE TABLE buy -- 구매 테이블
(  num 		INT AUTO_INCREMENT NOT NULL PRIMARY KEY, -- 순번(PK)
   mem_id  	CHAR(8) NOT NULL, -- 아이디(FK)
   prod_name 	CHAR(6) NOT NULL, --  제품이름
   group_name 	CHAR(4)  , -- 분류
   price     	INT  NOT NULL, -- 가격
   amount    	SMALLINT  NOT NULL, -- 수량
   FOREIGN KEY (mem_id) REFERENCES member(mem_id)
);

INSERT INTO member VALUES('TWC', '트와이스', 9, '서울', '02', '11111111', 167, '2015.10.19');
INSERT INTO member VALUES('BLK', '블랙핑크', 4, '경남', '055', '22222222', 163, '2016.08.08');
INSERT INTO member VALUES('WMN', '여자친구', 6, '경기', '031', '33333333', 166, '2015.01.15');
INSERT INTO member VALUES('OMY', '오마이걸', 7, '서울', NULL, NULL, 160, '2015.04.21');
INSERT INTO member VALUES('GRL', '소녀시대', 8, '서울', '02', '44444444', 168, '2007.08.02');
INSERT INTO member VALUES('ITZ', '잇지', 5, '경남', NULL, NULL, 167, '2019.02.12');
INSERT INTO member VALUES('RED', '레드벨벳', 4, '경북', '054', '55555555', 161, '2014.08.01');
INSERT INTO member VALUES('APN', '에이핑크', 6, '경기', '031', '77777777', 164, '2011.02.10');
INSERT INTO member VALUES('SPC', '우주소녀', 13, '서울', '02', '88888888', 162, '2016.02.25');
INSERT INTO member VALUES('MMU', '마마무', 4, '전남', '061', '99999999', 165, '2014.06.19');

INSERT INTO buy VALUES(NULL, 'BLK', '지갑', NULL, 30, 2);
INSERT INTO buy VALUES(NULL, 'BLK', '맥북프로', '디지털', 1000, 1);
INSERT INTO buy VALUES(NULL, 'APN', '아이폰', '디지털', 200, 1);
INSERT INTO buy VALUES(NULL, 'MMU', '아이폰', '디지털', 200, 5);
INSERT INTO buy VALUES(NULL, 'BLK', '청바지', '패션', 50, 3);
INSERT INTO buy VALUES(NULL, 'MMU', '에어팟', '디지털', 80, 10);
INSERT INTO buy VALUES(NULL, 'GRL', '혼공SQL', '서적', 15, 5);
INSERT INTO buy VALUES(NULL, 'APN', '혼공SQL', '서적', 15, 2);
INSERT INTO buy VALUES(NULL, 'APN', '청바지', '패션', 50, 1);
INSERT INTO buy VALUES(NULL, 'MMU', '지갑', NULL, 30, 1);
INSERT INTO buy VALUES(NULL, 'APN', '혼공SQL', '서적', 15, 1);
INSERT INTO buy VALUES(NULL, 'MMU', '지갑', NULL, 30, 4);

SELECT * FROM member;
SELECT * FROM buy;

```

> **데이터 베이스 만들기**
> ```sql
> DROP DATABASE IF EXISTS market_db;
> CREATE DATABASE market_db;
> ```
> 1. `DROP DATABASE`는 market_db를 삭제하는 문장입니다. 만약 이미 market_db가 존재하면 삭제합니다.
> 2. 데이터베이스를 새로 만듭니다.

> **회원 테이블(member) 만들기**
> ```sql
> USE market_db;
> CREATE TABLE member -- 회원 테이블
> ( mem_id  		CHAR(8) NOT NULL PRIMARY KEY, -- 사용자 아이디(PK)
>   mem_name    	VARCHAR(10) NOT NULL, -- 이름
>   mem_number    INT NOT NULL,  -- 인원수
>   addr	  		CHAR(2) NOT NULL, -- 지역(경기,서울,경남 식으로 2글자만입력)
>   phone1		CHAR(3), -- 연락처의 국번(02, 031, 055 등)
>   phone2		CHAR(8), -- 연락처의 나머지 전화번호(하이픈제외)
>   height    	SMALLINT,  -- 평균 키
>   debut_date	DATE  -- 데뷔 일자
> );
> ```
> (SQL에서 하이픈(-) 두 개는 주석으로 인식합니다.)
> 1. `USE`문은 market_db 데이터베이스를 선택하는 문장입니다.
> 2. `CREATE ~ );`는 member 테이블을 만드는 과정입니다.

> **구매 테이블(buy) 만들기**
> ```sql
> CREATE TABLE buy -- 구매 테이블
> (  num 		INT AUTO_INCREMENT NOT NULL PRIMARY KEY, -- 순번(PK)
>    mem_id  	CHAR(8) NOT NULL, -- 아이디(FK)
>    prod_name 	CHAR(6) NOT NULL, --  제품이름
>    group_name 	CHAR(4)  , -- 분류
>    price     	INT  NOT NULL, -- 가격
>    amount    	SMALLINT  NOT NULL, -- 수량
>    FOREIGN KEY (mem_id) REFERENCES member(mem_id)
> );
> ```
> 1. 구매 테이블을 생성합니다.
> 2. AUTO_INCREMENT는 자동으로 숫자를 입력해준다는 의미입니다.

> **데이터 입력하기**
> ```sql
> INSERT INTO member VALUES('TWC', '트와이스', 9, '서울', '02', '11111111', 167, '2015.10.19');
> INSERT INTO buy VALUES(NULL, 'BLK', '지갑', NULL, 30, 2);
> ```
> 1. 회원 테이블(member)에 값을 입력합니다. CHAR, VARCHAR, DATE형은 작은 따옴표로 값을 묶어줬습니다. INT형은 작은 따옴표 없이 그냥 넣어주면 됩니다.
> 2. 구매 테이블(buy)의 첫 번째 열인 순번(num)은 자동으로 입력되므로 NULL이라고 써주면 됩니다.

> **데이터 조회하기**
> ```sql
> SELECT * FROM member;
> SELECT * FROM buy;
> ```

### 3-1-2. 기본 조회하기: SELECT ~ FROM

#### USE문

* SELECT 문을 실행하려면 먼저 사용할 데이터베이스를 지정해야 합니다. 현재 사용하는 데이터베이스를 지정 또는 변경하는 형식은 다음과 같습니다.

```sql
USE 데이터베이스_이름;
```

#### SELECT 문의 기본 형식

```sql
SELECT 열_이름
    FROM 테이블_이름
    WHERE 조건식
    GROUP BY 열_이름
    HAVING 조건식
    ORDER BY 열_이름
    LIMIT 숫자
```

이중 가장 핵심적인 형식은 다음과 같습니다.

```sql
SELECT 열_이름
    FROM 테이블_이름
    WHERE 조건식
```

#### SELECT와 FROM

* `SELECT * FROM member;` : 테이블에서 모든 열(*)을 가져옵니다.
  
* 원래 테이블의 전체 이름은 **데이터베이스_이름.테이블_이름** 형식으로 표현합니다. 하지만 데이터베이스 이름을 생략하면 USE 문으로 지정해 놓은 데이터베이스가 자동으로 선택됩니다. 따라서 `SELECT * FROM market_db.member;`와 같은 의미를 가집니다.

* 특정 열을 가져오기 위해서는 SELECT와 FROM 사이에 원하는 열_이름을 작성하며, 여러 개일 경우에는 콤마(,)로 구분하고, 원하는 순서대로 나열할 수 있습니다.

```sql
SELECT addr, debut_date, mem_name
    FROM member;
```

**열 이름 다음에 지정하고 싶은 별칭(alias)를 입력할 수 있습니다.** Output은 별칭으로 된 열로 출력합니다. 별칭에 공백이 있다면 큰따옴표(")로 묶어줍니다.

```sql
SELECT addr 주소, debut_date "데뷔 일자", mem_name
    FROM member;
```

### 3-1-3. 특정한 조건만 조회하기: SELECT ~ FROM ~ WHERE

#### WHERE 없이 조회하기

* 조건 없이 모든 자료를 불러오면 리소스를 많이 소모하게 됩니다. 따라서 WHERE절을 함께 사용합니다.

#### 기본적인 WHERE 절

* WHERE 절은 조회하는 결과에 특정한 조건을 추가해서 원하는 데이터만 보고 싶을 때 사용합니다.

```sql
SELECT 열_이름 FROM 테이블_이름 WHERE 조건식;
```
또는
```sql
SELECT 열_이름
    FROM 테이블_이름
    WHERE 조건식;
```

* 지금 찾는 이름(mem_name)이 '블랙핑크'라면 다음과 같이 작성합니다. **열_이름 = 값**은 열의 값에 해당하는 결과만 출력해줍니다.

```sql
SELECT * FROM member WHERE mem_name = '블랙핑크';
```

#### 관계 연산자, 논리 연산자의 사용

* 숫자로 표현된 데이터는 범위를 지정할 수 있습니다. 예를 들어 평균 키(height)가 162 이하인 회원을 검색하려면 다음과 같이 **관계 연산자**를 사용해서 조회할 수 있습니다.

```sql
SELECT mem_id, mem_name
    FROM member
    WHERE height <= 162;
```

* 2가지 이상의 조건을 만족하도록 하기 위해선 **논리 연산자(AND, OR)** 를 이용해서 조회할 수 있습니다.

```sql
SELECT mem_name, height, mem_number
    FROM member
    WHERE height >= 165 AND mem_number > 6;
```

#### BETWEEN ~ AND

* 범위에 있는 값을 구하는 경우에 `BETWEEN ~ AND`를 사용해도 됩니다.

```sql
SELECT mem_name, height
    FROM member
    WHERE height BETWEEN 163 AND 165;
```

#### IN()

* 주소 등의 문자로 표현된 데이터는 여러 문자 중 하나에 포함되는지 비교하는 기능인 IN()을 사용할 수 있습니다

```sql
SELECT mem_name, addr
    FROM member
    WHERE addr IN('경기', '전남', '경남');
```

#### LIKE

* 문자열의 일부 글자를 검색하려면 LIKE를 사용합니다. "우%"와 같은 표현은 제일 앞 글자가 "우"인 모든 값을 허용한다는 뜻입니다.

```sql
SELECT *
    FROM member
    WHERE mem_name LIKE '우%';
```

* 한 글자와 매치하기 위해서는 **언더바(_)** 를 사용합니다.

```sql
SELECT *
    FROM member
    WHERE mem_name LIKE '__핑크';
```

### 3-1-4. 서브 쿼리

* SELECT 안에 또 다른 SELECT가 들어갈 수 있습니다.

* 예를 들어, SQL을 통해 에이핑크의 평균 키(height)를 알아보면

```sql
SELECT height FROM member WHERE mem_name = '에이핑크';
```

* 에이핑크의 평균 키를 알았으니 이 평균 키를 통해 164보다 키가 큰 회원을 조회하면 됩니다.

```sql
SELECT mem_name, height FROM member WHERE height > 164;
```

* 이 두 SQL을 하나로 만드는 것도 가능합니다.

```sql
SELECT mem_name, height FROM member
    WHERE height > (SELECT height FROM member WHERE mem_name = '에이핑크');
```

## 3-2. 좀 더 깊게 알아보는 SELECT문

* SELECT문에서는 결과의 정렬을 위한 **ORDER BY**, 결과의 개수를 제한하는 **LIMIT**, 중복된 데이터를 제거하는 **DISTINCT** 등을 사용할 수 있습니다.

* **GROUP BY** 절은 지정한 열의 데이터들을 같은 데이터끼리 묶어서 결과를 추출합니다. 주로 그룹으로 묶는 경우는 합계, 평균, 개수 등을 처리할 때 사용하므로 집계 함수와 함께 사용합니다. GROUP BY 절에서도 HAVING 절을 통해 조건식을 추가할 수 있습니다. **HAVING**절은 WHERE 절과 비슷해보이지만 GROUP BY 절과 함께 사용되는 것이 차이점입니다.

### 3-2-1. ORDER BY 절

```sql
SELECT 열_이름
    FROM 테이블_이름
    WHERE 조건식
    GROUP BY 열_이름
    HAVING 조건식
    ORDER BY 열_이름
    LIMIT 숫자
```

* ORDER BY 절은 결과가 출력되는 순서를 조절합니다.

```sql
SELECT 열_이름
    FROM 테이블_이름
    ORDER BY 열_이름;
```

* 기준 열을 오름차순으로 정리하기 위해서는 **ASC**를, 아닌 내림차순으로 정리하기 위해서는 **DESC**를 제일 뒤에 붙여줍니다.

```sql
SELECT 열_이름
    FROM 테이블_이름
    ORDER BY 열_이름 DESC;
```

* ORDER BY 절도 WHERE절과 함께 사용하여 조건에 맞는 값을 추출해 순서대로 데이터를 확인할 수 있습니다.

```sql
SELECT 열_이름
    FROM 테이블_이름
    WHERE 조건식
    ORDER BY 열_이름;
```

* 그런데 종종, 기준 열의 행 값이 같은 데이터가 있을 수 있는데, 이럴 때 또 다른 기준으로 정렬하기 위해서 여러 개의 열이 필요할 때가 있습니다. 이럴 때는 콤마(,)를 통해 원하는 순서에 따라 열을 적어주면 됩니다.

```sql
SELECT 열_이름
    WHERE 조건식
    ORDER BY 첫_번째_열, 두_번째_열;
```

#### 출력의 개수를 제한: LIMIT

* **LIMIT**는 출력하는 개수를 제한합니다.

```sql
SELECT 열_이름
    FROM 테이블_이름
    LIMIT 제한 개수;
```

* ORDER BY와 함께 정렬한 후 사용하는 것이 일반적입니다.

* LIMIT 형식은 **LIMIT 시작, 개수**입니다. `LIMIT 3`과 같이 쓸 때는 `LIMIT 0, 3`과 동일한 의미입니다. 즉, 0번째부터 3건이라는 의미입니다.

* LIMIT 시작, 개수는 **LIMIT 개수 OFFSET 시작**이라고 쓰는 것과 동일합니다. 또한 LIMIT는 첫 데이터를 0번으로 설정하고 시작합니다.

#### 중복된 결과를 제거: DISTINCT

* **DISTINCT**는 조회된 결과에서 중복된 데이터를 1개만 남깁니다. 열 이름 앞에 DISTINCT를 써주기만 하면 중복된 데이터를 1개만 남기고 제거합니다.

```sql
SELECT DISTINCT 열_이름 FROM 테이블_이름;
```

### 3-2-2. GROUP BY 절

* GROUP BY 절은 말 그대로 그룹으로 묶어주는 역할을 합니다. 집계함수는 주로 GROUP BY 절과 함께 쓰이며, 데이터를 그룹화(grouping)해주는 기능을 합니다.

#### 집계 함수

> * SUM(): 합계를 구합니다.
> * AVG(): 평균을 구합니다.
> * MIN(): 최솟갑을 구합니다.
> * MAX(): 최댓값을 구합니다.
> * COUNT(): 행의 개수를 셉니다.
> * COUNT(DISTINCT): 행의 개수를 셉니다(중복은 1개만 인정).

* 각 회원별로 구매한 개수를 합쳐서 출력하기 위해서는 집계함수인 SUM()과 GROUP BY 절을 사용하면 됩니다. 즉, GROUP BY로 회원별로 묶어준 후에 SUM() 함수로 구매한 개수를 합치면 됩니다.

```sql
SELECT mem_id, SUM(amount) FROM buy GROUP BY mem_id;
```

* 전체 회원이 구매한 물품 개수의 평균을 구하기 위해서 `SELECT AVG(amount) "평균 구매 개수" FROM buy`를 하고, 그룹별 평균을 위해서는 `SELECT mem_id, AVG(amount) "평균 구매 개수" FROM buy GROUP BY mem_id;`와 같이 표현하는데 GROUP BY의 유무에 따라 달라지는 것을 확인할 수 있습니다.

#### HAVING 절

* SELECT 문에서 WHERE를 통해 조건에 맞는 데이터만 보고 싶은 경우가 있었습니다. 이때 GROUP BY를 사용하는 경우에는 HAVING을 통해 집계함수에 대해서 조건을 제한합니다.

```sql
SELECT 열_이름
    FROM 테이블_이름
        GROUP BY 열_이름
        HAVING 조건식;
```

```sql
SELECT mem_id "회원 아이디", SUM(price*amount) "총 구매 금액"
	  FROM buy
        GROUP BY mem_id
        HAVING SUM(price*amount) > 1000;
```

## 3-3. 데이터 변경을 위한 SQL문

* 데이터베이스와 테이블을 만든 후에는 데이터를 변경하는, 즉 입력/수정/삭제하는 기능이 필요합니다.

* 새로운 데이터를 테이블에 입력할 때는 **INSERT**, 데이터를 수정할 때는 **UPDATE**, 데이터를 삭제할 때는 **DELETE**문을 사용합니다.

### 3-3-1. 데이터 입력: INSERT

#### INSERT 문의 기본 문법

* INSERT는 테이블에 데이터를 삽입하는 명령입니다. 

```sql
INSERT INTO 테이블 [(열1, 열2, ...)] VALUES (값1, 값2, ...)
```

테이블 이름 나음에 나오는 열은 생략이 가능합니다. 생략할 경우 VALUES의 값들이 열 순서 및 개수와 동일해야 합니다.

```sql
USE market_db;
CREATE TABLE hongong1 (toy_id INT, toy_name CHAR(4), age INT);
INSERT INTO hongong1 VALUES (1, '우디', 25);
```

열의 순서를 바꿔서 입력하거나 원하는 열에만 정보를 입력하고 싶다면 테이블 이름 뒤에 열 이름을 기입하여 SQL을 작성한다.

```sql
INSERT INTO hongong1 (toy_id, toy_name) VALUES (2, '버즈');
```

#### 자동으로 증가하는 AUTO_INCREMENT

* AUTO_INCREMENT는 열을 정의할 때 1부터 증가하는 값을 입력해줍니다. 주의할 점은 AUTO_INCREMENT로 지정하는 열은 꼭 **PRIMARY KEY**로 지정해줘야 합니다.

```sql
CREATE TABLE hongong2 (
  toy_id INT AUTO_INCREMENT PRIMARY KEY,
  toy_name CHAR(4),
  age INT
);
```

이제 데이터를 입력할 때, 자동 증가하는 부분은 NULL 값으로 채워 놓으면 됩니다.

* 만약 AUTO_INCREMENT로 입력되는 다음 값을 100부터 시작하도록 변경하고 싶다면 다음과 같이 실행합니다.

```sql
ALTER TABLE hongong2 AUTO_INCREMENT=100;
INSERT INTO hongong2 VALUES (NULL, '재남', 35);
SELECT * FROM hongong2;
```

ALTER TABLE은 테이블을 변경하라는 의미입니다.  
  
혹은 처음부터 입력되는 값을 1000으로 지정하고, 다음 값으로 3씩 증가하도록 설정하는 방법을 살펴보겠습니다.  
  
시스템 변수인 `@@auto_increment_increment`를 변경시켜야 합니다.

```sql
CREATE TABLE hongong3 (
    toy_id INT AUTO_INCREMENT PRIMARY KEY,
    toy_name CHAR(4),
    age INT);
ALTER TABLE hongong3 AUTO_INCREMENT=1000;
SET @@auto_increment_increment=3;
```

* INSERT INTO 문은 1줄로 작성할 수도 있습니다.

```sql
INSERT INTO 테이블_이름 VALUES (값1, 값2, ...), (값3, 값4, ...);
```

#### 다른 테이블의 데이터를 한 번에 입력하는 INSERT INTO ~ SELECT

* 다른 테이블에 이미 데이터가 입력되어 있다면 **INSERT INTO ~ SELECT** 구문을 사용해 해당 테이블의 데이터를 가져와서 한 번에 입력할 수 있습니다.

```sql
INSERT INTO 테이블_이름 (열_이름1, 열_이름2, ...)
    SELECT 문;
```

주의할 것은 SELECT 문의 열 개수가 INSERT할 테이블의 열 개수와 같아야 한다는 것입니다.

* DESC는 Describe의 약자로, 테이블 구조를 출력해주는 기능을 합니다.

### 3-3-2. 데이터 수정: UPDATE

* 회원의 정보가 변경되는 경우 UPDATE를 사용해서 내용을 수정합니다.

#### UPDATE 문의 기본 문법

* **UPDATE**는 기존에 입력되어 있는 값을 수정하는 명령입니다.

```sql
UPDATE 테이블_이름
    SET 열1=값1, 열2=값2, ...
    WHERE 조건 ;
```

```sql
USE market_db;
UPDATE city_popul
  SET city_name = '서울'
  WHERE city_name = 'Seoul';
SELECT * FROM city_popul WHERE city_name = '서울';
```

city_popul이라는 테이블에서 city_name이 'Seoul'인 데이터를 '서울'로 바꿔줍니다(SET).  
  
* 필요하면 한꺼번에 여러 열의 값을 변경할 수 있습니다. 콤마(,)로 분리해서 여러 개의 열을 변경하면 됩니다.

```sql
UPDATE city_popul
    SET city_name = '뉴욕', population = 0
    WHERE city_name = 'New York';
SELECT * FROM city_popul WHERE city_name = '뉴욕';
```

SET에는 변경할 값을 입력하고, WHERE는 데이터 조건을 두어 원하는 데이터만 바꿀 수 있도록 합니다.

#### WHERE가 없는 UPDATE문

* UPDATE문에서 **WHERE** 절은 문법상 생략이 가능하지만, WHERE 절을 생략하면 테이블의 모든 행의 값이 변경됩니다.

`SET city_name = '서울';`은 WHERE를 사용하지 않으면 모든 데이터의 city_name이 '서울'로 바꿔버릴 것입니다.

* 값을 일괄적으로 바꾸는 경우는 인구의 단위를 10,000명 단위로 바꾸는 등의 과정을 위해 사용하는 경우도 있습니다.

```sql
UPDATE city_popul
    SET population = population / 10000;
SELECT * FROM city_popul LIMIT 5;
```

## 3-3-3. 데이터 삭제: DELETE

* 데이터를 삭제할 때 **DELETE**를 사용하여 행 데이터를 삭제합니다.

```sql
DELETE FROM 테이블_이름 WHERE 조건;
```

```sql
DELETE FROM city_popul
    WHERE city_name LIKE 'New%';
```

WHERE 조건을 만족하는 모든 데이터를 삭제하고 싶은 것이 아니라, 상위 몇 건만 삭제하려면 LIMIT를 사용합니다.

## 3-3-4. 대용량 테이블의 삭제

* 대용량 테이블을 `DELETE`, `DROP`, `TRUNCATE`라는 3가지 방법으로 삭제하는 방법이 있습니다.

* DELETE문은 삭제가 오래 걸립니다. DROP 문은 데이터 자체를 삭제합니다. TRUNCATE 문도 DELETE와 동일한 효과를 내지만 속도가 무척 빠릅니다. DROP과 달리 빈 테이블을 남깁니다.

```sql
DELETE FROM 테이블_이름;
DROP TABLE 테이블_이름;
TRUNCATE TABLE 테이블_이름;
```

# Chapter 4. SQL 고급 문법

## 4-1. MySQL의 데이터 형식

### 4-1-1. 데이터 형식

#### 정수형

정수형은 소수점이 없는 숫자입니다.

* TINTINT: 바이트 수 - 1, 숫자 범위 - (-128 ~ 127)
* SMALLINT: 바이트 수 - 2, 숫자 범위 - (-32,768 ~ 32,767)
* INT: 바이트 수 - 4, 숫자 범위 - (약 -21억 ~ 21억)
* BIGINT: 바이트 수 - 8, 숫자 범위 - (약 -900경 ~ 900경)

값의 범위를 0 이상으로 할 때는 값의 범위가 0부터 시작되는 **`UNSIGNED`** 예약어를 사용할 수 있습니다. 1바이트는 256개를 표현하므로 -128~127로 표현하거나, 0~255로 표현하거나 모두 256개를 표현하는 것입니다.

#### 문자형

문자형은 글자를 저장하기 위해 사용하며, 입력할 최대 글자의 개수를 지정해야 합니다.

* CHAR(개수): 바이트 수 - 1~255
* VARCHAR(개수): 바이트 수 - 1~16383

CHAR은 Character의 약자로, 고정길이 문자형이라고 부릅니다. 즉, 자릿수가 고정되어 있습니다. 이와 달리 VARCHAR(Variable Character)는 가변길이 문자형으로, VARCHAR(10)에 '가나다' 3글자를 저장할 경우 3자리만 사용합니다.  

**VARCHAR가 CHAR보다 공간을 효율적으로 운영**할 수 있지만, MySQL 내부적으로 성능(빠른 속도)면에서는 CHAR로 설정하는 것이 조금 더 좋습니다.

따라서 글자의 개수가 고정된 경우에는 CHAR를, 글자의 개수가 변동될 경우에는 VARCHAR를 사용하는 것이 좋습니다.

데이터 중에서는 숫자지만 문자형으로 데이터에 저장하는 경우가 있습니다(ex. 전화번호). 숫자형으로 의미를 갖기 위해서는 **연산에 의미가 있거나, 대소 순서에 의미가 있어야 합니다.** 

#### 대량의 데이터 형식

텍스트 데이터의 바이트가 CHAR와 VARCHAR보다 클 때, 이렇게 큰 데이터를 저장하려면 다음과 같은 형식을 사용합니다.

* TEXT 형식
  - TEXT: 바이트 수 1 ~ 65535
  - LONGTEXT: 바이트 수 1 ~ 4294967295
* BLOB 형식
  - BLOB: 바이트 수 1 ~ 65535
  - LONGBLOG: 바이트 수 1 ~ 4294967295

TEXT 형식의 경우 소설이나 영화 대본과 같은 내용을 저장한다면 필요한 데이터 형식입니다.

BLOB은 Binary Long Object의 약자로 글자가 아닌 이미지, 동영상 등의 데이터라고 생각하면 됩니다. 이런 것을 이진(Binary) 데이터라고 부릅니다. 테이블에 이미지나 동영상과 같은 것을 저장하고 싶다면 BLOB이나 LONGBLOB로 데이터 형식을 지정해야 합니다.

#### 실수형

실수형은 소수점이 있는 숫자를 저장할 때 사용합니다.

* FLOAT: 바이트 수 - 4, 소수점 아래 7자리까지 표현
* DOUBLE: 바이트 수 - 8, 소수점 아래 15자리까지 표현

#### 날짜형

날짜형은 날짜 및 시간을 저장할 때 사용합니다.

* DATE: 바이트 수 - 3, 날짜만 저장. YYYY-MM-DD 형식으로 사용
* TIME: 바이트 수 - 3, 시간만 저장. HH:MM:SS 형식으로 사용
* DATETIME: 바이트 수 - 8, 날짜 및 시간을 저장. YYYY-MM-DD HH:MM:SS 형식으로 사용

날짜 또는 시간을 입력할 때는 문자와 마찬가지로 작은 따옴표로 묶어줘야 합니다.

### 4-1-2. 변수의 사용

```sql
SET @변수이름 = 변수의 값 ;  -- 변수의 선언 및 값 대입
SELECT @변수이름 ; -- 변수의 값 출력
```

변수는 MySQL 워크벤치를 재시작할 때까지는 유지되지만, 종료하면 없어집니다.

```sql
USE market_db;
SET @myVar1 = 5 ;
SET @myVar2 = 4.25 ;

SELECT @myVar1 ;
SELECT @myVar1 + @myVar2;

SET @txt = "가수 이름==> " ;
SET @height = 166 ;
SELECT @txt, mem_name FROM member WHERE height > @height ;
```

행의 개수를 제한하는 LIMIT에는 변수를 사용할 수 없기 떄문에 문법상 오류를 발생시킵니다.

이를 해결하는 것이 **`PREPARE`**와 **`EXECUTE`**입니다. PREPARE는 실행하지 않고 SQL 문만 준비해놓고 EXECUTE에서 실행하는 방식입니다.

```sql
SET @count = 3;
PREPARE mySQL FROM 'SELECT mem_name, height FROM member ORDER BY height LIMIT ?';
EXECUTE mySQL USING @count;
```
PREPARE는 mySQL이라는 이름으로 준비만 해놓습니다. **?** 는 현재는 모르지만 나중에 채워진다는 의미입니다. EXECUTE로 mySQL에 저장된 SELECT문을 실행할 때, USING으로 물음표에 @count 변수의 값을 대입하는 것입니다.

### 4-1-3. 데이터 형 변환

문자형을 정수형으로 바꾸거나, 정수형을 문자형으로 바꾸는 것을 데이터의 **형 변환(type conversion)** 이라고 부릅니다. 형 변환에는 직접 함수를 사용해서 변환하는 **명시적인 변환(explicit conversion)** 과 별도의 지시 없이 자연스럽게 변환되는 **암시적인 변환(implicit conversion)** 이 있습니다.

#### 함수를 이용한 명시적인 변환

데이터 형식을 변환하는 함수는 `CAST()`, `CONVERT()`입니다. 둘은 형식만 다를 뿐 동일한 기능을 합니다.

```sql
CAST ( 값 AS 데이터_형식 [ (길이) ] )
CONVERT ( 값, 데이터_형식 [ (길이) ] )
```

예를 들어 가격을 평균할 때 웬만하면 정수보다 실수로 계산되곤 합니다. 하지만, 가격은 실수보다 정수로 표현하는 것이 더 보기 좋습니다. CAST()와 CONVERT()를 사용해 정수로 표현하도록 합니다. 함수에 올 수 있는 데이터 형식은 **CHAR, SIGNED, UNSIGNED, DATE, TIME, DATETIME 등**입니다. SIGNED는 부호가 있는 정수, UNSIGNED는 부호가 없는 정수를 의미합니다.

```sql
SELECT CAST(AVG(price) AS SIGNED) '평균 가격' FROM buy;
-- 또는
SELECT CONVERT(AVG(price), SIGNED) '평균 가격' FROM buy;
```

다양한 구분자를 날짜형으로 변경할 수도 있습니다.

```sql
SELECT CAST('2022$12$12' AS DATE);
SELECT CAST('2022/12/12' AS DATE);
SELECT CAST('2022%12%12' AS DATE);
SELECT CAST('2022@12@12' AS DATE);
```

CONCAT()은 문자를 이어주는 역할을 합니다. 정수형을 문자형으로 CAST 혹은 CONVERT 하여 사용하는 방법이 있습니다.

#### 암시적인 변환

암시적인 변환은 자엽스럽게 형이 변환되는 것입니다.

```sql
SELECT '100' + '200' ;
300
```

문자는 더할 수 없으므로 자동으로 숫자로 변환해서 덧셈을 수행합니다. 이것은 CONCAT도 마찬가지로 정수형과 문자형을 이을 때 자동으로 정수형이 변환되어 출력됩니다.

## 4-2. 두 테이블을 묶는 조인

* 조인(join)이란 두 개의 테이블을 서로 묶어서 하나의 결과를 만들어 내는 것을 말합니다.

### 4-2-1. 내부 조인

#### 일대다 관계의 이해

두 테이블의 조인을 위해서는 테이블이 **일대다(one to many)** 관계로 연결되어야 합니다. 데이터베이스의 테이블은 여러 정보를 주제에 따라 분리해서 저장하는 것이 효율적입니다. 이 분리된 테이블은 서로 **관계**를 갖고 있습니다.  

일대다 관계란 한쪽 테이블에는 하나의 값만 존재해야 하지만, 연결된 다른 테이블에는 여러 개의 값이 존재할 수 있는 관계를 말합니다. 일대다 관계에서 주로 '일'의 데이터를 갖는 테이블에서 식별할 열을 **기본 키(Primary Key, PK)** '다'의 테이블에서 기본 키에 상응하는 열을 **외래 키(Foreign Key, FK)**라고 합니다.

#### 내부 조인의 기본

대부분의 조인은 2개로 조인합니다. 기본적인 형식은 다음과 같습니다.

```sql
SELECT <열 목록>
FROM <첫 번째 테이블>
  INNER JOIN <두 번째 테이블>
  ON <조인될 조건>
[WHERE 검색 조건]
```

본 교재에서 사용한 sql문입니다.

```sql
USE market_db;
SELECT *
	FROM buy
    INNER JOIN member
    ON buy.mem_id = member.mem_id
WHERE buy.mem_id = 'GRL';
```

첫 번째 테이블은 buy 테이블이며, 두 번째 테이블은 member 테이블입니다. 조인될 조건은 buy 테이블과 member 테이블의 mem_id가 같은 조건일 때이며, buy.mem_id 가 'GRL'인 것만 추출해서 보겠다는 의미입니다.

#### 내부 조인의 간결한 표현

```sql
SELECT mem_id, mem_name, prod_name, addr, CONCAT(phone1, phone2) '연락처'
	FROM buy
		INNER JOIN member
        ON buy.mem_id = member.mem_id;
```
이렇게 표현할 시 **mem_id**가 어느 테이블의 열인지 명확하지 않기 때문에 **테이블_이름.열_이름**으로 표기합니다.

하지만 모든 열을 테이블_이름.열_이름으로 하는 것은 코드도 길어지고 가독성도 떨어지게 됩니다. 이를 간결하게 하기 위해 FROM 절에 나오는 테이블의 이름 뒤에 **별칭**을 부여합니다.

```sql
SELECT B.mem_id, M.mem_name, B.prod_name, M.addr, CONCAT(M.phone1, M.phone2) '연락처'
	FROM buy B
		INNER JOIN member M
        ON B.mem_id = M.mem_id;
```

#### 내부 조인의 활용

내부 조인을 사용하면 두 테이블에 모두 있는 내용만 조인되는 방식입니다. 만약, **양쪽 중에 한곳이라도 내용이 있을 때 조인**하려면 **외부조인**을 사용해야 합니다.

#### 중복된 결과 1개만 출력하기

앞서 배운 DISTINCT 문을 사용해 출력되는 데이터를 중복 없이 확인할 수 있습니다.

```sql
SELECT DISTINCT M.mem_id, M.mem_name, M.addr
	FROM buy B
		INNER JOIN member M
        ON B.mem_id = M.mem_id
	ORDER BY M.mem_id;
```

### 4-2-2. 외부 조인

* 내부 조인은 두 테이블에 모두 데이터가 있어야만 결과가 나옵니다. 이와 달리 외부 조인은 한 쪽에만 데이터가 있어도 결과가 나옵니다.

#### 외부 조인의 기본

외부 조인은 두 테이블을 조인할 때 필요한 내용이 한 테이블에만 있어도 결과를 추출할 수 있습니다.

```sql
SELECT <열 목록>
FROM <첫 번째 테이블(LEFT 테이블)>
  <LEFT | RIGHT | FULL> OUTER JOIN <두 번째 테이블(RIGHT 테이블)>
  ON <조인될 조건>
[WHERE 검색 조건];
```

```sql
SELECT M.mem_id, M.mem_name, B.prod_name, M.addr
	FROM member M
		LEFT OUTER JOIN buy B
        ON M.mem_id = B.mem_id
	ORDER BY M.mem_id;
```

LEFT OUTER JOIN 문의 의미를 '왼쪽 테이블(member)의 내용은 모두 출력되어야 한다' 정도로 해석하면 기억하기 쉽습니다.

RIGHT OUTER JOIN으로 동일한 결과를 출력하고자 한다면 다음과 같이 작성할 수 있습니다.

```sql
SELECT M.mem_id, M.mem_name, B.prod_name, M.addr
	FROM buy B
		RIGHT OUTER JOIN member M
        ON M.mem_id = B.mem_id
	ORDER BY M.mem_id;
```
이것은 JOIN의 기준이 member로 동일하기 때문입니다.

#### 외부 조인의 활용

외부 조인을 통해 NULL 값을 추출해낼 수도 있습니다. 쇼핑몰 데이터베이스에서 한 번도 구매하지 않은 고객을 찾아내는 등에 응용할 수 있습니다.

```sql
SELECT M.mem_id, M.mem_name, B.prod_name, M.addr
	FROM member M
		LEFT OUTER JOIN buy B
        ON M.mem_id = B.mem_id
	WHERE B.prod_name IS NULL
    ORDER BY M.mem_id;
```

**FULL OUTER JOIN**은 왼쪽 외부 조인과 오른쪽 외부 조인이 합쳐진 것이라고 생각하면 됩니다.

### 4-2-3. 기타 조인

#### 상호 조인

**상호 조인**은 한쪽 테이블의 모든 행과 다른 쪽 테이블의 모든 행을 조인시키는 기능을 말합니다. 그래서 **상호 조인 결과의 전체 행 개수는 두 테이블의 각 행의 개수를 곱한 개수**가 됩니다.

```sql
SELECT *
	FROM buy
		CROSS JOIN member;
```

* ON 구문을 사용할 수 없습니다.
* 결과의 내용은 의미가 없습니다. 랜덤으로 조인하기 때문입니다(서로 의미 없는 데이터끼리 조인되곤 합니다).
* 상호 조인의 주 용도는 테스트하기 위해 대용량의 데티어를 생성할 때입니다.

#### 자체 조인

자체 조인은 자신이 자신과 조인한다는 의미입니다. 그래서 자체 조인은 1개의 테이블을 사용합니다.

```sql
SELECT <열 목록>
FROM <테이블> 별칭 A
  INNER JOIN <테이블> 별칭 B
  ON <조인될 조건>
[WHERE 검색 조건];
```

```sql
SELECT A.emp "직원", B.emp "직속상관", B.phone "직속상관연락처"
	FROM emp_table A
		INNER JOIN emp_table B
        ON A.manager = B.emp
	WHERE A.emp = '경리부장';
```

## 4-3. SQL 프로그래밍

스토어드 프로시저는 MySQL에서 프로그래밍 기능이 필요할 때 사용하는 데이터베이스 개체입니다.

```sql
DELIMITER $$
CREATE PROCEDURE 스토어드_프로시저_이름()
BEGIN
  SQL 프로그래밍 코딩
END $$ -- 스토어드 프로시저 종료
DELIMITER ; -- 종료 문자를 다시 세미콜론으로 변경
CALL 스토어드_프로시저_이름() -- 스토어드 프로시저 실행
```
### 4-3-1. IF문

#### IF문의 기본 형식

```sql
IF <조건식> THEN
  SQL 문장들
END IF;
```

'SQL 문장들'이 한 문장이라면 그 문장만 써도 되지만, 두 문장 이상이 처리되어야 할 때는 `BEGIN~END`로 묶어줘야 합니다.

```sql
DROP PROCEDURE IF EXISTS ifProc1;
DELIMITER $$
CREATE PROCEDURE ifProc1()
BEGIN
	IF 100 = 100 THEN
		SELECT '100은 100과 같습니다.';	
	END IF;
END $$
DELIMITER ;
CALL ifProc1;
```

#### IF ~ ELSE 문

참일 때와 더불어 거짓일 때 실행할 SQL문을 입력합니다.

```sql
DROP PROCEDURE IF EXISTS ifProc2;
DELIMITER $$
CREATE PROCEDURE ifProc2()
BEGIN
	DECLARE myNum INT;
    SET myNum = 200;
    IF myNum = 100 THEN
		SELECT '100입니다.';
	ELSE
		SELECT '100이 아닙니다.';
	END IF;
END $$
DELIMITER ;
CALL ifProc2;
```

#### IF 문의 활용

```sql
DROP PROCEDURE IF EXISTS ifProc3;
DELIMITER $$
CREATE PROCEDURE ifProc3()
BEGIN
	DECLARE debutDate DATE; -- 데뷔일자
    DECLARE curDate DATE; -- 오늘
    DECLARE days INT; -- 활동한 일수
    SELECT debut_date INTO debutDate
		FROM market_db.member
        WHERE mem_id = 'APN';
	
    SET curDate = CURRENT_DATE(); -- 현재 날짜
    SET days = DATEDIFF(curDate, debutDate); -- 날짜의 차이, 일 단위
    
    IF (days/365) >= 5 THEN -- 5년이 지낫다면
		SELECT CONCAT('데뷔한 지 ', days, '일이나 지났습니다. 핑순이들 축하합니다!');
	ELSE
		SELECT '데뷔한 지 ' + days + '일밖에 안되었네요. 핑순이들 화이팅~';
	END IF;
END $$
DELIMITER ;
CALL ifProc3 ;
```

SELECT INTO 변수는 결과를 변수에 저장합니다. CURRENT_DATE() 함수로 현재 날짜를 curDate에 저장합니다. DATEDIFF() 함수로 데뷔 일자부터 현재 날짜까지 일수를 days에 저장했습니다.(CURRENT_TIMESTAMP()는 오늘 날짜 및 시간을 함께 알려줍니다.)

### 4-3-2. CASE 문

여러 조건 중에서 선택하는 경우 CASE 문을 사용합니다.

#### CASE 문의 기본 형식

CASE 문은 2가지 이상의 여러 가지 경우일 때 처리가 가능하므로 '다중 분기'라고 부릅니다.

```sql
CASE
  WHEN 조건1 THEN
    SQL 문장들1
  WHEN 조건2 THEN
    SQL 문장들2
  WHEN 조건3 THEN
    SQL 문장들3
  ELSE
    SQL 문장들4
END CASE;
```
모든 조건에 해당하지 않으면 ELSE를 실행합니다. 학점을 나누는 경우를 예로 들어보겠습니다.

```sql
DROP PROCEDURE IF EXISTS caseProc;
DELIMITER $$
CREATE PROCEDURE caseProc()
BEGIN
	DECLARE point INT ;
    DECLARE credit CHAR(1);
    SET point = 88;
    
    CASE
		WHEN point >= 90 THEN
			SET credit = 'A';
		WHEN point >= 80 THEN
			SET credit = 'B';
		WHEN point >= 70 THEN
			SET credit = 'C';
		WHEN point >= 60 THEN
			SET credit = 'D';
		ELSE
			SET credit = 'F';
	END CASE;
    SELECT CONCAT('취득점수==>', point), CONCAT('학점==>', credit);
END $$
DELIMITER ;
CALL caseProc();
```

#### CASE 문의 활용

CASE 문의 활용입니다. 총 구매액이 1500 이상인 경우 최우수 고객, 1000 ~ 1499일 경우 우수 고객, 1 ~ 999는 일반 고객, 0 이하는 유령 고객으로 세그먼트를 만들겠습니다.

```sql
SELECT mem_id, SUM(price*amount) "총 구매액"
	FROM buy
    GROUP BY mem_id;
```
추가적으로 구매액으로 내림차순 정렬합니다.
```sql
SELECT mem_id, SUM(price*amount) "총 구매액"
	FROM buy
    GROUP BY mem_id
    ORDER BY SUM(price*amount) DESC;
```
회원의 이름을 출력하기 위해 구매 테이블과 조인합니다.
```sql
SELECT B.mem_id, M.mem_name, SUM(price*amount) "총 구매액"
	FROM buy B
		INNER JOIN member M
        ON B.mem_id = M.mem_id
    GROUP BY B.mem_id
    ORDER BY SUM(price*amount) DESC;
```
구매하지 않은 회원의 아이디와 이름도 출력해보겠습니다.
```sql
SELECT M.mem_id, M.mem_name, SUM(price*amount) "총 구매액"
	FROM buy B
		RIGHT OUTER JOIN member M
        ON B.mem_id = M.mem_id
    GROUP BY M.mem_id
    ORDER BY SUM(price*amount) DESC;
```
이제 CASE문을 활용해 회원등급을 지정합니다.
```sql
SELECT M.mem_id, M.mem_name, SUM(price*amount) "총 구매액",
		CASE
			WHEN (SUM(price*amount) >= 1500) THEN '최우수고객'
            WHEN (SUM(price*amount) >= 1000) THEN '우수고객'
            WHEN (SUM(price*amount) >= 1) THEN '일반고객'
            ELSE '유령고객'
		END "회원등급"
	FROM buy B
		RIGHT OUTER JOIN member M
        ON B.mem_id = M.mem_id
    GROUP BY M.mem_id
    ORDER BY SUM(price*amount) DESC;
```
### 4-3-3. WHILE 문

WHILE문은 필요한 만큼 계속 같은 내용을 반복할 수 있습니다.

#### WHILE 문의 기본 형식

```sql
DROP PROCEDURE IF EXISTS whileProc;
DELIMITER $$
CREATE PROCEDURE whileProc()
BEGIN
	DECLARE i INT; -- 1에서 100까지 증가할 변수
    DECLARE hap INT; -- 더한 값을 누적할 변수
    SET i = 1;
    SET hap = 0;
    
    WHILE (i <= 100) DO
		SET hap = hap + i; -- hap의 원래 값에 i를 더해서 다시 hap에 넣으라는 의미
        SET i = i + 1;     -- i의 원래 값에 1을 더해서 다시 i에 넣으라는 의미
	END WHILE;
	
    SELECT '1부터 100까지의 합==>', hap;
END $$
DELIMITER ;
CALL whileProc();
```

#### WHILE 문의 응용

1에서 100까지의 합계에서 4의 배수를 제외시키려면 어껗게 해야 할까요? 추가로 숫자를 더하는 중간에 합계가 1,000이 넘는 순간의 숫자를 출력한 후 프로그램을 종료하고 싶다면 어떻게 해야 할까요? 이런 경우에 **ITERATE**문과 **LEAVE**문을 활용할 수 있습니다.

* ITERATE[레이블]: 지정한 레이블로 가서 계속 진행합니다.
* LEAVE[레이블]: 지정한 레이블을 빠져나갑니다. 즉 WHILE 문이 종료됩니다.

```sql
DROP PROCEDURE IF EXISTS whileProc2;
DELIMITER $$
CREATE PROCEDURE whileProc2()
BEGIN
	DECLARE i INT; -- 1에서 100까지 증가할 변수
    DECLARE hap INT; -- 더한 값을 누적할 변수
    SET i = 1;
    SET hap = 0;
    
    myWhile: -- 레이블 지정
    WHILE (i <= 100) DO
		IF(i%4 = 0) THEN
			SET i = i + 1;
            ITERATE myWhile; -- 지정한 label 문으로 가서 계속 진행
		END IF;
        SET hap = hap + i;
        IF (hap > 1000) THEN
			LEAVE myWhile; -- 지정한 label 문을 떠남. 즉 While 종료
		END IF;
        SET i = i + 1;
	END WHILE;
    
    SELECT '1부터 100까지의 합(4의 배수 제외), 1000 넘으면 종료 ==>', hap;
END $$
DELIMITER ;
CALL whileProc2();
```
WHILE 문을 myWhile이라는 레이블로 지정했습니다. i가 4의 배수라면 i를 1증가시키고 ITERATE를 만나서 `myWhile:`로 올라갑니다. 즉, WHILE 문을 계속 진행합니다. hap이 1000을 초과하면 myWhile 레이블을 빠져나갑니다.

### 4-3-4. 동적 SQL

SQL 문은 내용이 고정되어 있는 경우가 대부분입니다. 하지만 상황에 따라 내용 변경이 필요할 때 동적 SQL을 사용하면 변경되는 내용을 실시간으로 적용시켜 사용할 수 있습니다.

#### PREPARE와 EXECUTE
**PREPARE**는 SQL 문을 실행하지는 않고 미리 준비해놓고, **EXECUTE**는 준비한 SQL 문을 실행합니다. 그리고 실행 후에는 **DEALLOCATE PREPARE**로 문장을 해제해주는 것이 바람직합니다.

```sql
USE market_db;
PREPARE myQuery FROM 'SELECT * FROM member WHERE mem_id = "BLK"';
EXECUTE myQuery;
DEALLOCATE PREPARE myQuery;
```
PREPARE 문에서는 `SELECT * FROM member WHERE mem_id = "BLK"`를 바로 실행하지 않고 myQuery에 입력만 시켜놓습니다. 실행이 필요한 시점에서 `EXECUTE myQuery`문으로 실행합니다

이렇게 미리 SQL을 준비한 후에 나중에 실행할 것을 동적 SQL이라고 부릅니다.

#### 동적 SQL의 활용

PREPARE 문에서는 ?로 향후에 입력될 값을 비워 놓고, EXECUTE에서 USING으로 ?에 값을 전달할 수 있습니다.

```sql
DROP TABLE IF EXISTS gate_table;
CREATE TABLE gate_table (
	id INT AUTO_INCREMENT PRIMARY KEY,
    entry_time DATETIME);

SET @curDate = CURRENT_TIMESTAMP(); -- 현재 날짜와 시간

PREPARE myQuery FROM 'INSERT INTO gate_table VALUES(NULL, ?)';
EXECUTE myQuery USING @curDate;
DEALLOCATE PREPARE myQuery;

SELECT * FROM gate_table;
```

일반 SQL에서 변수는 @변수명으로 지정하는데 별도의 선언은 없어도 됩니다. 스토어드 프로시저에서 변수는 DECLARE로 선언한 후에 사용해야 합니다.

# Chapter 5. 테이블과 뷰

## 5-1. 테이블 만들기

테이블: 행(row, record)과 열(column, field)로 구성된 2차원 구조

### 5-1-1. 데이터베이스와 테이블 설계하기

테이블을 만들기 위해 테이블을 설계한다. 테이블 이름, 열 이름, 데이터 형식, 기본 키를 적절히 지정하여 설계한다.

### 5-1-2. GUI 환경에서 테이블 만들기

#### 데이터 베이스 생성하기

```sql
CREATE DATABASE 데이터베이스_이름;
```

#### 테이블 생성하기

GUI 에서는 기본 키-외래 키 관계를 선택할 수 없다.

#### 데이터 입력하기

기본 키와 외래 키 관계인 열의 레이블에서 기본 키 열에 없는 데이터가 외래 키에 있으면 안 된다. **외래 키에 있는 값은 반드시 기본 키에도 있어야 한다.**

### 5-1-3. SQL로 테이블 만들기

#### 데이터베이스 생성하기

```sql
CREATE DATABASE naver_db;
```

#### 테이블 생성하기

```sql
CREATE TABLE member -- 회원 테이블
( mem_id		CHAR(8) NOT NULL PRIMARY KEY, -- 회원 아이디(PK)
  mem_name		VARCHAR(10) NOT NULL, -- 이름
  mem_number	TINYINT NOT NULL, -- 인원수
  addr			CHAR(2) NOT NULL, -- 주소(경기, 서울, 경남 식으로 2글자만 입력)
  phone1		CHAR(3) NULL, -- 연락처의 국번(02, 031, 055 등)
  phone2        CHAR(8) NULL, -- 연락처의 나머지 전화번호(하이픈 제외)
  height		TINYINT UNSIGNED NULL, -- 평균 키
  debut_date	DATE NULL -- 데뷔 일자
);
```
테이블을 기본적으로 갖춘 뒤, NOT NULL 혹은 NULL을 입력하고 PRIMARY KEY를 입력한다.

AUTO_INCREMENT로 지정한 열은 **PRIMARY KEY**나 **UNIQUE**로 꼭 지정해야 한다.

```sql
FOREIGN KEY(mem_id) REFERENCES member(mem_id)
```

FK의 기준이 되는 PK열을 REFERENCES를 통해 연결한다.

#### 데이터 입력하기

```sql
INSERT INTO member VALUES('TWC', '트와이스', 9, '서울', '02', '11111111', 167, '2015-10-19');
INSERT INTO member VALUES('BLK', '블랙핑크', 4, '경남', '055', '22222222', 163, '2016-8-8');
INSERT INTO member VALUES('WMN', '여자친구', 6, '경기', '031', '33333333', 166, '2015-1-15');
```

## 5-2. 제약조건으로 테이블을 견고하게

테이블을 만들 때 테이블의 구조에 필요한 제약조건을 설정해줘야 하는데, 앞에서 확인한 기본 키와 외래 키가 대표적인 제약조건이다.

이메일, 휴대폰 등 중복되지 않는 열에는 고유 **키(Unique)** 를 지정할 수 있다. 또한, 실수로 값을 올바르지 않게 입력하는 것을 방지하는 제약조건이 **체크(Check)** 이다. 제약조건으로 **기본값(Default)** 을 설정할 수도 있고, **NOT NULL**도 제약조건으로 설정할 수 있다

### 5-2-1. 제약조건의 기본 개념과 종류

**제약조건**은 데이터의 무결성을 지키기 위해 제한하는 조건이다. 데이터의 결함이 없는 것을 **데이터의 무결성**이라고 표현한다.

* PRIMARY KEY 제약조건

* FOREIGN KEY 제약조건
  
* UNIQUE 제약조건

* CHECK 제약조건

* DEFAULT 정의

* NULL 값 허용

### 5-2-2. 기본 키 제약조건

데이터를 구분할 수 있는 식별자를 **기본 키(Primary Key)** 라고 부른다. 기본 키에 입력되는 값은 **중복될 수 없으며, NULL 값이 입력될 수 없다.**

대부분의 테이블은 기본 키를 가져야 한다. 물론, 기본 키가 없어도 테이블 구성이 가능하지만 실무에서 사용하는 테이블에는 기본 키를 설정해야 중복된 데이터가 입력되지 않는다. 기본 키로 생성한 것은 자동으로 **클러스터형 인덱스**가 생성된다. 기본 키는 하나의 열에만 설정해야 하기 때문에 테이블의 특성을 가장 잘 반영하는 열을 선택하는 것이 좋다.

#### CREATE TABLE에서 설정하는 기본 키 제약조건

열 이름 뒤에 PRIMARY KEY를 입력하여 기본 키로 설정하면 설정한 열에 입력되는 데이터는 중복될 수 없고, 비어 있을 수도 없다.

**기본 키-외래 키 관계로 연결된 테이블은 외래 키가 설정된 테이블을 먼저 삭제해야 한다.** 기본 키 테이블이 삭제되면 외래 키 테이블에서 데이터를 알 수 없기 때문.

기본 키는 제일 마지막 행에 `PRIMARY KEY (열_이름)`을 통해 지정할 수도 있다.

#### ALTER TABLE에서 설정하는 기본 키 제약조건

제약조건을 설정하는 또 다른 방법은 이미 만들어진 테이블을 수정하는 ALTER TABLE 구문을 사용하는 것이다.

```sql
ALTER TABLE member -- 1. member를 변경
	ADD CONSTRAINT -- 2. 제약조건 추가
    PRIMARY KEY (mem_id); -- 3. mem_id 열에 기본 키 제약조건을 설정
```

> **기본 키에 이름 지정하기**
> 
> 기본 키의 이름을 직접 지어줄 수도 있다.  
> `CONSTRAINT PRIMARY KEY PK_member_mem_id (mem_id)`

### 5-2-3. 외래 키 제약조건

외래 키 제약조건은 두 테이블 사이의 관계를 연결해주고 그 결과 데이터의 무결성을 보장해주는 역할을 한다. 외래 키가 설정된 열은 꼭 다른 테이블의 기본 키와 연결된다.

기본 키가 있는 테이블을 **기준 테이블**이라고 부르며, 외래 키가 있는 구매 테이블을 **참조 테이블**이라고 부른다.

구매 테이블과 회원 테이블이 서로 기본 키-외래 키 관계일 때, 구매 테이블의 데이터는 모두 누구인지 알 수 있는 무결한 데이터가 되는 것이다.

참조 테이블이 참조하는 기준 테이블의 열은 반드시 **기본 키나 고유 키로 설정**되어 있어야 한다.

#### CREATE TABLE에서 설정하는 외래 키 제약조건

CREATE TABLE 끝에 FOREIGN KEY 키워드를 설정하는 것으로 생성한다.

`FOREIGN KEY(열_이름) REFERENCES 기준_테이블(열_이름)`이 기본 형식으로 참조할 기준 테이블의 열은 Primary Key 또는 Unique여야만 한다.(꼭 열 이름이 같을 필요는 없음)

#### ALTER TABLE에서 설정하는 외래 키 제약조건

```sql
ALTER TABLE buy -- 1. buy를 수정한다.
	ADD CONSTRAINT -- 2. 제약조건을 추가한다.
	FOREIGN KEY(mem_id) -- 3. 외래 키 제약조건을 buy 테이블의 mem_id에 설정한다.
    REFERENCES member(mem_id); -- 4. 참조할 기준 테이블은 member 테이블의 mem_id 열이다.
```

#### 기준 테이블의 열이 변경될 경우

기준 테이블 열의 데이터를 변경하고자 할 때 오류가 발생한다. 열 이름이 변경되면 참조 테이블의 데이터에 문제가 발생하기 때문이다(만약 참조 테이블에 기준 테이블 열 데이터가 없다면 변경 가능). 같은 이유로 삭제도 불가능하다. 기준 테이블의 열 이름이 변경될 때 참조 테이블의 열 이름이 자동으로 변경되는 것이 더 효율적일 것이다.

이를 위해 **`ON UPDATE CASCADE`** 와 **`ON DELETE CASCADE`** 문을 통해 자동으로 변경되도록 할 수 있다.

```sql
ALTER TABLE buy
  ADD CONSTRAINT
  FOREIGN KEY(mem_id) REFERENCES member(mem_id)
  ON UPDATE CASCADE
  ON DELETE CASCADE
```
ALTER TABLE에서 입력하고 수정 및 삭제를 해도 참조 테이블이 자동으로 적용되는 것을 볼 수 있다.

### 5-2-4. 기타 제약조건

#### 고유 키 제약조건

고유 키 제약조건은 '**중복되지 않는 유일한 값**'을 입력해야 하는 조건이다. 기본 키 제약조건과 다른 점은 **NULL 값을 허용**한다는 것이다. 또한, 기본 키와 달리 **여러 개를 설정**할 수 있다.

#### 체크 제약조건

체크 제약조건은 입력되는 데이터를 점검하는 기능을 한다. 열의 정의 뒤에 CHECK(조건)을 추가해주면 된다.

```sql
...
height  TINYINT UNSIGNED NULL CHECK (height >= 100)
...
```
혹은 테이블을 만든 후에 ALTER TABLE 문으로 제약조건을 추가해도 된다.
```sql
ALTER TABLE member
	ADD CONSTRAINT
    CHECK (phone1 IN ('02', '031', '032', '054', '055', '061'));
```

#### 기본값 정의

기본값 정의는 값을 입력하지 않았을 때 자동으로 입력될 값을 미리 지정해 놓는 방법이다. 열을 정의할 때 옆에 `DEFAULT 데이터`와 같이 작성한다. ALTER TABLE 문에 작성해도 동일한 효과를 갖는다.

```sql
ALTER TABLE member
	ALTER COLUMN phone1 SET DEFAULT '02';
```

열에 지정할 떄는 **`ALTER COLUMN`** 을 사용하여 DEFALUT를 작성하도록 한다.

기본값이 설정된 열에 기본값을 입력하려면 **default**라고 써주고, 원하는 값을 입력하려면 해당 값을 써주면 된다.

#### NULL 값 허용

널값을 허용하려면 생략하거나 NULL을 사용하고, 허용하지 않으려면 NOT NULL을 사용한다.