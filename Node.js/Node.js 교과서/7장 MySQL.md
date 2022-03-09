- [7.1 데이터베이스란?](#71-데이터베이스란)
- [7.2 MySQL 설치](#72-mysql-설치)
- [7.4 데이터베이스 및 테이블 생성하기](#74-데이터베이스-및-테이블-생성하기)
  - [7.4.1 데이터베이스 생성하기](#741-데이터베이스-생성하기)
  - [7.4.2 테이블 생성하기](#742-테이블-생성하기)
    - [자료형](#자료형)
    - [자료형의 옵션](#자료형의-옵션)
    - [테이블 자체에 대한 설정](#테이블-자체에-대한-설정)
- [7.5 CRUD 작업하기](#75-crud-작업하기)
  - [7.5.1 Create(생성)](#751-create생성)
  - [7.5.2 Read(조회)](#752-read조회)
  - [7.5.3 Update(수정)](#753-update수정)
  - [7.5.4 Delete(삭제)](#754-delete삭제)
- [7.6 시퀄라이즈 사용하기](#76-시퀄라이즈-사용하기)
  - [7.6.1 MySQL 연결하기](#761-mysql-연결하기)
  - [7.6.2 모델 정의하기](#762-모델-정의하기)
  - [7.6.3 관계 정의하기](#763-관계-정의하기)

# 7.1 데이터베이스란?

**데이터베이스**는 관련성을 가지며 중복이 없는 데이터들의 집합이다. 이러한 데이터베이스를 관리하는 시스템을 DBMS(DataBase Management System)(데이터베이스 관리 시스템)라고 부른다.

보통 서버의 하드 디스크나 SSD 등의 저장 매체에 데이터를 저장한다. 사용자가 직접 데이터를 지우지 않는 이상 데이터가 보존되므로 데이터를 지속적으로 사용할 수 있다.

데이터베이스를 관리하는 DBMS 중에서 RDBMS(Relational DBMS)라고 부르는 관계형 DBMS가 많이 사용된다. RDBMS로는 Oracle, MySQL, MSSQL 등이 있다.

# 7.2 MySQL 설치

# 7.4 데이터베이스 및 테이블 생성하기

## 7.4.1 데이터베이스 생성하기
```
$ mysql -h localhost -u root -p
```
로 sql에 접속한 후, `CREATE SCHEMA [데이터베이스명]`로 데이터베이스를 생성한다. 이후 `use nodejs;` 명령어를 추가로 입력하여 nodejs로 이름 지은 데이터베이스를 사용하겠다고 MySQL에 알린다.

`CREATE SCHEMA` 뒤에 `DEFAULT CHARACTER SET utf8;`을 붙여 한글을 사용할 수 있게 만든다.

## 7.4.2 테이블 생성하기

테이블이란 데이터가 들어갈 수 있는 틀을 의미하며, 테이블에 맞는 데이터만 들어갈 수 있다.

```sql
CREATE TABLE nodejs.users (
    id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(20) NOT NULL,
    age INT UNSIGNED NOT NULL,
    married TINYINT NOT NULL,
    comment TEXT NULL,
    created_at DATETIME NOT NULL DEFAULT now(),
    PRIMARY KEY(id),
    UNIQUE INDEX name_UNIQUE (name ASC))
    COMMENT = '사용자 정보'
    DEFAULT CHARACTER SET = utf8
    ENGINE = InnoDB;
```

* `CREATE TABLE [데이터베이스명.테이블명]`: 테이블을 생성하는 명령어

순서대로 id(고유 식별자), name(이름), age(나이), married(결혼 여부), comment(자기소개), created_at(로우 생성일)이다.

### 자료형

* INT: 정수. 소수까지 저장하고 싶다면 FLOAT이나 DOUBLE 자료형 사용

* VARCHAR(자릿수), CHAR(자릿수): CHAR는 고정길이, VARCHAR는 가변길이.

* TEXT: 긴 글을 저장할 때 사용.

* TINYINT: -128부터 127까지의 정수를 저장할 때 사용. 1 또는 0만 저장한다면 불값(Boolean)과 같은 역할을 할 수 있다.

* DATETIME: 날짜와 시간에 대한 정보를 담고 있다. 날짜 정보만 담는 DATE와 시간 정보만 담는 TIME 자료형도 있다.

---
### 자료형의 옵션

* NULL, NOT NULL: 빈칸 허용 여부

* AUTO_INCREMENT: 숫자가 자동으로 올라간다는 의미

* UNSIGNED: 숫자 자료형에 적용되는 옵션. 숫자 자료형은 기본적으로 음수 범위를 지원한다. UNSIGNED가 적용되어 있으면 음수가 무시된다(그만큼 양수 값을 더 많이 받을 수 있음). FLOAT와 DOUBLE에는 UN 적용이 불가능하다.

* ZEROFILL: 숫자의 자릿수가 고정되어 있을 때 사용. 가끔 자료형 INT 대신 INT(자릿수)처럼 표현하는 경우가 있는데, ZEROFILL로 설정해둔다면 비어 있는 자리에 모두 0을 넣는다. 

* DEFAULT: 데이터베이스 저장 시 해당 컬럼에 값이 없다면 MySQL이 기본값을 대신 넣는다. now()는 현재 시각을 넣으라는 뜻이다. now() 대신 CURRENT_TIMESTAMP를 적어도 같은 값이 된다.

* PRIMARY KEY: 기본 키 컬럼을 설정한다. 로우들을 구별할 고유한 식별자가 필요하기 때문에 설정한다. MySQL에는 PRIMARY KEY(id)라는 옵션으로 id 컬럼이 기본 키임을 알렸다.

* UNIQUE INDEX: 해당 값이 고유해야 하는지에 대한 옵션이며, name 컬럼이 해당된다. 인덱스의 이름은 name_UNIQUE로, name 컬럼을 오름차순(ASC)으로 기억하겠다는 것이다. PRIMARY KEY나 UNIQUE INDEX의 경우 데이터베이스가 별도로 컬럼을 관리하므로 조회 시 속도가 빨라진다. 기본 키인 id도 고유해야 하지만 PRIMARY KEY는 자동으로 UNIQUE INDEX를 포함하므로 따로 적지 않아도 된다.

---

### 테이블 자체에 대한 설정

* COMMENT: 테이블에 대한 보충 설명. 이 테이블이 무슨 역할을 하는지 적어두면 된다.

* DEFAULT CHARACTER SET utf8: 한글을 입력하기 위해 반드시 설정한다.

* ENGINE은 여러 가지가 있지만, MyISAM과 InnoDB가 제일 많이 사용된다.

---

comments 테이블에는 id, commenter(댓글을 쓴 사용자 아이디), comment(댓글 내용), created_at(로우 생성일) 컬럼이 있다.

commenter 컬럼에는 댓글을 작성한 사용자의 id를 저장할 것이다. 이렇게 다른 테이블의 기본 키를 저장하는 칼럼을 **외래 키(foreign key)** 라고 부른다. `CONSTRAINT [제약조건명] FOREIGN KEY [컬럼명] REFERENCES [참고하는 칼럼명]`으로 외래 키를 지정할 수 있다.

comments 테이블에서는 commenter 컬럼과 users 테이블의 id 컬럼을 연결했다. 다른 테이블의 기본 키이므로 comment 컬럼에 인덱스도 걸었다.

그후 `ON UPDATE`와 `ON DELETE` 모두 `CASCADE`로 설정하여, 사용자 정보가 수정되거나 삭제되면 그것과 연결된 댓글 정보도 같이 수정하거나 삭제되도록 하였다.

# 7.5 CRUD 작업하기

CRUD는 Create, Read, Update, Delete의 첫 글자를 모은 두문자어로 데이터베이스에서 많이 수행하는 네 가지 작업이다.

## 7.5.1 Create(생성)

Create(생성)는 데이터를 생성해서 데이터베이스에 넣는 작업이다. users 테이블에 데이터를 몇 개 넣어본다.

`INSERT INTO [테이블명] ([컬럼1], [컬럼2], ...) VALUES ([값1], [값2], ...);`를 통해 데이터를 넣도록 한다.

## 7.5.2 Read(조회)

`SELECT * FROM [테이블명]` 형식으로 테이블의 모든 데이터를 조회한다.

* 특정 컬럼만 조회할 수도 있다. SELECT 다음에 조회할 컬럼을 콤마로 찍어 조회한다.

* `WHERE`절을 사용하면 특정 조건을 가진 데이터만 조회할 수도 있다.

* WHERE절에서 AND는 조건이 모두 참인 데이터만, OR은 조건들 중 어느 하나라도 만족하는 데이터를 찾는다.

* `ORDER BY [컬렴명] [ASC|DESC]` 키워드를 사용하면 정렬도 가능하다. ASC는 오름차순, DSEC는 내림차순이다.

* `LIMIT [숫자]` 키워드는 조회할 로우 개수를 설정한다.

* 로우 개수를 설정하면서 몇 개를 건너뛸지 설정할 수도 있다. `OFFSET [건너뛸 숫자]` 키워드를 사용한다.

## 7.5.3 Update(수정)

`UPDATE [테이블명] SET [컬렴명=바꿀 값] WHERE [조건]`을 통해 정보를 수정할 수 있다.

## 7.5.4 Delete(삭제)

`DELETE FROM [테이블명] WHERE [조건]`으로 데이터를 삭제할 수 있다. 

# 7.6 시퀄라이즈 사용하기

시퀄라이즈는 ORM(Object-relational Mapping)으로 분류된다. ORM은 자바스크립트 객체와 데이터베이스의 릴레이션을 매핑해주는 도구이다.

시퀄라이즈를 쓰는 이유는 자바스크립트 구문을 알아서 SQL로 바꿔주기 때문이다. 따라서 SQL 언어를 직접 사용하지 않아도 자바스크립트만으로 MySQL을 조작할 수 있고, SQL을 몰라도 MySQL을 어느 정도 다룰 수 있게 된다.

```
$ npm i express morgan nunjucks sequelize sequelize-cli mysql2
$ npm i -D nodemon
```

sequelize-cli는 시퀄라이즈 명령어를 처리하기 위한 패키지, mysql2는 MySQL과 시퀄라이즈를 이어주는 드라이버이다. 

Sequelize는 시퀄라이즈 패키지이자 생성자이다. config/config.json에서 데이터베이스 설정을 불러온 후 new Sequelize를 통해 MySQL 연결 객체를 생성한다.

## 7.6.1 MySQL 연결하기

db.sequelize를 불러와서 sync 메서드를 사용해 서버 실행 시 MySQL과 연동되도록 했다. 내부에 force: false 옵션이 있는데, 이 옵션을 true로 설정하면 서버 실행 시마다 테이블을 재생성한다. 테이블을 잘못 만든 경우에 true로 설정하면 된다.

MySQL과 연동할 때 config 폴더 안의 config.json 정보가 사용된다. development.password와 development.database를 현재 MySQL 커넥션과 일치하게 수정하면 된다. test와 production 쪽은 각각 테스트 용도와 배포 용도로 접속하기 위해 사용되는 것이다.

이 설정은 process.env.NODE_ENV가 development일 때 적용된다(기본적으로 development). 나중에 배포할 때는 process.env.NODE_ENV를 production으로 설정해둔다. 따라서 배포 환경을 위해 데이터베이스를 설정할 때는 config/config.json의 production 속성을 수정하면 된다.

## 7.6.2 모델 정의하기

시퀄라이즈는 모델과 MySQL의 테이블을 연결해주는 역할을 한다. User와 Comment 모델을 만들어 users 테이블과 comments 테이블에 연결해보자.

User 모델을 만들고 모듈로 exports했다. Sequelize.Model을 확장한 클래스로 선언한다. 패턴만 숙지하면 된다. 모델은 크게 **static init 메서드와 static associate 메서드**로 나뉜다.

* init 메서드에는 테이블에 대한 설정을 하고, associate 메서드에는 다른 모델과의 관계를 적는다.

* init 메서드의 첫 번째 인수가 테이블 컬럼에 대한 설정, 두 번째 인수가 테이블 자체에 대한 설정이다. 시퀄라이즈는 id를 기본 키로 연결하므로 id 칼럼은 적어줄 필요가 없다.

**시퀄라이즈의 자료형**

VARCHAR은 STRING으로, INT는 INTEGER로, TINYINT는 BOOLEAN으로, DATETIME은 DATE로 적는다. INTEGER.UNSIGNED는 UNSIGNED 옵션이 적용된 INT를 의미한다. ZEROFILL 옵션도 사용하고 싶다면 INTEGER.UNSIGNED.ZEROFILL을 적는다.

allowNull은 NOT NULL 옵션과 동일하다. unique는 UNIQUE 옵션이다. defaultValue는 기본값(DEFAULT)을 의미한다. Sequelize.NOW로 현재 시간을 기본 값으로 사용할 수 있다.

super init 메서드의 두 번째 인수는 테이블 옵션이다.

* sequelize: static init 메서드의 매개변수와 연결되는 옵션으로 db.sequalize 객체를 넣어야 한다.

* timestamps: 현재 false로 되어 있으며, 이 속성 값이 true면 시퀄라이즈는 createAt과 updateAt 컬럼을 추가한다. 각각 로우가 생성될 때와 수정될 때의 시간이 자동으로 입력된다. 하지만, 예제에서는 직접 create_at 컬럼을 만들었으므로 필요하지 않다.

* underscored: 시퀄라이즈는 기본적으로 테이블명과 컬럼명을 캐멀 케이스로 만든다.

* modelName: 모델 이름을 설정할 수 있다. 노드 프로젝트에서 사용.

* tableName: 실제 데이터베이스의 테이블 이름이 된다.

* paranoid: true로 설정하면 deleteAt이라는 컬럼이 생긴다. 로우를 삭제할 때 완전히 지워지지 않고 deleteAt에 지운 시각이 기록된다. 로우를 조회하는 명령을 내렸을 때는 deleteAt의 값이 null인 로우를 조회한다. 나중에 로우를 복원하기 위해서이다.

* charset과 collate: 각각 utf8, utf8_general_ci로 설정해야 한글이 입력된다.

db라는 객체에 User와 Comment 모델을 담아두었다. 앞으로 db 객체를 require하여 User와 Comment 모델에 접근할 수 있다. User.init과 Comment.init은 각각의 모델의 static.init 메서드를 호출하는 것이다. init이 실행되어야 테이블이 모델로 연결된다. 다른 테이블과의 관계를 연결하는 associate 메서드도 미리 실행해둔다.

## 7.6.3 관계 정의하기