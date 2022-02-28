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