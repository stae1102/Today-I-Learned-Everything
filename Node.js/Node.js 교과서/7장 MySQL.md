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
    - [7.6.3.1 1:N](#7631-1n)
    - [7.6.3.2 1:1](#7632-11)
    - [7.6.3.3 N:M](#7633-nm)
  - [7.6.4 쿼리 알아보기](#764-쿼리-알아보기)
    - [로우를 생성하는 쿼리](#로우를-생성하는-쿼리)
    - [로우를 조회하는 쿼리](#로우를-조회하는-쿼리)
    - [로우를 수정하는 쿼리](#로우를-수정하는-쿼리)
    - [로우를 삭제하는 쿼리](#로우를-삭제하는-쿼리)
    - [7.6.4.1 관계 커리](#7641-관계-커리)
    - [7.6.4.2 SQL 쿼리하기](#7642-sql-쿼리하기)
  - [7.6.5 쿼리 수행하기](#765-쿼리-수행하기)

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

사용자 한 명은 댓글을 여러 개 작성할 수 있다. 하지만 댓글 하나에 사용자가 여러 명일 수는 없다. 이러한 관계를 **일대다(1:N)** 관계라고 한다.

일대일 관계로는 사용자와 사용자에 대한 정보 테이블을 예로 들 수 있다. 사용자 한 명은 자신의 정보를 담고 있는 테이블과만 관계가 있다. 정보 테이블도 한 사람만을 가리킨다. 이러한 관계를 일대일(1:1) 관계라고 한다.

다대다 관계로는 게시글 테이블과 해시태그 테이블 관계를 예로 들 수 있다. 한 게시글에 여러 개의 해시태그가 달릴 수도 있고, 한 해시태그도 여러 게시글이 달릴 수 있다. 이러한 관계를 다대다(N:M) 관계라고 한다.

### 7.6.3.1 1:N

시퀄라이즈에서 1:N 관계를 hasMany라는 메서드로 표현한다. users 테이블의 로우 하나를 불러올 때 comments의 로우들도 같이 불러올 수 있다. 반대로 belongsTo 메서드도 있다. comments 테이블의 로우를 불러올 때 users 테이블의 로우를 가져온다.

다른 모델의 정보가 들어가는 테이블에 belongsTo를 사용한다. 시퀄라이즈는 모델 간 관계를 파악해서 Comment 모델에 foreignKey인 commenter 칼럼을 추가한다. User 모델의 id 컬럼을 가리키고 있다.

sourceKey의 id와 targetKey의 id 모두 User 모델의 id이다. hasMany에서는 sourceKey를 쓰고, belongsTo에서는 targetKey를 쓴다고 생각하면 된다.

foreignKey를 따로 지정하지 않는다면 이름이 모델명+기본 키인 컬럼이 모델에 생성된다.

### 7.6.3.2 1:1

hasOne 메서드를 사용한다.

예를 들어 이렇게 사용할 수 있다.

```js
db.User.hasOne(db.Info, { foreignKey: 'UserId', sourceKey: 'id' });
db.Info.belongsTo(db.User, { foreignKey: 'UserId', sourceKey: 'id' });
```

### 7.6.3.3 N:M

belongsToMany 메서드를 사용한다.

```js
db.Post.belongsToMany(db.Hashtag, { through: 'PostHashtag' });
db.Hashtag.belongsToMany(db.Post, { through: 'PostHashtag' });
```

양쪽 모델에 모두 belongsToMany 메서드를 사용한다. N:M 관계의 특성상 새로운 모델이 생성된다. through 속성에 그 이름을 적으면 된다. N:M에서는 여러 단계를 거쳐 데이터를 조회해야 하는데, 위의 경우 Post에서 PostHashtag, PostHashtag에서 Hashtag로 정보를 가져온다. 자동으로 생성된 모델들도 `db.sequelize.models.PostHashtag`를 통해 접근할 수 있다.

## 7.6.4 쿼리 알아보기

시퀄라이즈로 CRUD 작업을 하려면 먼저 시퀄라이즈 쿼리를 알아야 한다. SQL문을 자바스크립트로 생성하는 것이라 시퀄라이즈만의 방식이 있다. 쿼리는 프로미스를 반환하므로 then을 붙여 결괏값을 받을 수 있다. async/await 문법과 같이 사용할 수도 있다.

### 로우를 생성하는 쿼리

```
INSERT INTO nodejs.users (name, age, married, comment) VALUES ('zero', 24, 0, '자기소개1');
↓
const { User } = require('../models');
User.create({
  name: 'zero',
  age: 24,
  married: false,
  comment: '자기소개1',
});
```

models 모듈에서 User 모델을 불러와 **create 메서드**를 사용하면 된다. 한 가지 주의할 점은 데이터를 넣을 때 MySQL의 자료형이 아니라 시퀄라이즈 모델에 정의한 자료형 대로 넣어야 한다는 것이다. 이것이 married가 0이 아니라 false인 이유이다. 시퀄라이즈가 알아서 MySQL 자료형으로 바꾼다. 자료형이나 옵션에 부합하지 않는 데이터를 넣었을 때는 시퀄라이즈가 에러를 발생시킨다.

### 로우를 조회하는 쿼리

**findAll 메서드**를 사용한다.

```
SELECT * FROM nodejs.users;
User.findAll({});
```

다음은 users 테이블의 데이터 하나만 가져오는 SQL문이다. 앞으로 데이터를 하나만 가져올 때는 **findOne 메서드**를, 여러 개 가져올 때는 **findAll 메서드**를 사용한다고 생각하면 된다.

```
SELECT * FROM nodejs.users LIMIT 1;
User.findOne({});
```

attribute 옵션을 사용해서 원하는 컬럼만 가져올 수도 있다.
```
SELECT name, married FROM nodejs.users;
User.findAll({
  attributes: ['name', 'married'],
});
```

where 옵션이 조건을 나열하는 옵션이다.

```
SELECT name, age FROM nodejs.users WHERE married = 1 AND age > 30;
const { Op } = require('sequelize');
const { User } = require('../models');
User.findAll({
  attributes: ['name', 'age'],
  where: {
    married: true,
    age: { [Op.gt]: 30 },
  },
});
```

시퀄라이즈는 자바스크립트 객체를 사용해서 쿼리를 생성해야 하므로 Op.gt 같은 특수한 연산자들이 사용된다. 

Op.gt(초과), Op.gte(이상), Op.lt(미만), Op.lte(이하), Op.ne(같지 않음), Op.or(또는), Op.in(배열 요소 중 하나), Op.notIn(배열 요소와 모두 다름) 등이 있다.

```
SELECT id, name FROM users WHERE married = 0 OR age > 30;
const { Op } = require('sequelize');
const { User } = require('../models');
User.findAll({
  attibutes: ['id', 'name'],
  where: {
    [Op.or]: [{ marred: false }, { age: { [Op.gt]: 30 } }],
  },
});
```

시퀄라이즈를 order 옵션을 통해 정렬할 수도 있다. 배열 안에 배열이 있다는 점에 주의해야 한다. 정렬은 컬럼 하나로 하는 것이 아니라 여러 개로 할 수 있기 때문이다.

```
SELECT id, name FROM users ORDER BY age DESC;
User.findAll({
  attributes: ['id', 'name'],
  order: [['age', 'DESC']],
});
```

조회할 로우 개수를 findAll 대신 findOne 메서드를 사용해도 되지만, 다음과 같이 limit 옵션으로 할 수도 있다.
```
SELECT id, name FROM users ORDER BY age DESC LIMIT 1;
User.findAll({
  attributes: ['id', 'name'],
  order: [['age', 'DESC']],
  limit: 1,
})
```
OFFSET도 역시 offset 속성으로 구현할 수 있다.
```
SELECT id, name FROM users ORDER BY age DESC LIMIT 1 OFFSET 1;
User.findAll({
  attributes: ['id', 'name'],
  order: ['age', 'DESC'],
  limit: 1,
  offset: 1,
});
```

### 로우를 수정하는 쿼리

```
UPDATE nodejs.users SET comment = '바꿀 내용' WHERE id = 2;
User.update({
  comment: '바꿀 내용',
}, {
  where: { id: 2 },
});
```

### 로우를 삭제하는 쿼리

```
DELETE FROM nodejs.users WHERE id = 2;
User.destroy({
  where: { id:2 },
});
```
destroy 메서드로 삭제하고 where 옵션에 조건을 적는다.

### 7.6.4.1 관계 커리

findOne이나 findAll 메서드를 호출할 때 프로미스의 결과로 모델을 반환한다(findAll 은 모두 찾는 것이므로 모델의 배열을 반환한다).

const user = await User.findOne({});
console.log(user.nick); 사용자 닉네임

User 모델의 정보에도 바로 접근할 수 있지만 더 편리한 점은 관계 쿼리를 지원한다는 것이다. MySQL로 따지면 JOIN 기능이다. **include** 속성을 사용한다.

```js
const user = await User.findOne({
  include: [{
    model: Comment,
  }]
});
console.log(user.Comments); // 사용자 댓글
```

**어떤 모델과 관계가 있는지를 include 배열에 넣어주면 된다.** 배열인 이유는 다양한 모델과 관계가 있을 수 있기 때문이다. 댓글은 여러 개일 수 있으므로(hasMany) user.Comments로 접근 가능하다. 또는 다음과 같이 댓글에 접근할 수도 있다.

```js
const user = await User.findOne({});
const comments = await user.getComments();
console.log(comments); // 사용자 댓글
```

관계를 설정했다면 getComments(조회), setComments(수정), addComment(하나 생성), addComments(여러 개 생성), removeComments(삭제) 메서드를 지원한다. **동사 뒤에 모델의 이름이 붙는 식이다.**

동사 뒤의 모델 이름을 바꾸고 싶다면 관계 설정 시 as 옵션을 사용할 수 있다.

```js
// 관계를 설정할 때 as로 등록
db.User.hasMany(db.Comment, { foreignKey: 'commenter', sourceKey: 'id', as: 'Answers'});
// 쿼리할 때는
const user = await User.findOne({});
const comments = await user.getAnswers();
console.log(comments); // 사용자 댓글
```

as를 설정하면 include 시 추가되는 댓글 객체도 user.Answer로 바뀐다.

include나 관계 쿼리 메서드에도 where나 attributes 같은 옵션을 사용할 수 있다.

```js
const user = await User.findOne({
  include: [{
    model: Comment,
    where: {
      id: 1,
    },
    attributes: ['id'],
  }]
});
// 또는
const comments = await user.getComments({
  where: {
    id: 1,
  },
  attributes: ['id'],
});
```

댓글을 가져올 때는 id가 1인 댓글만 가져오고, 컬럼도 id 컬럼만 가져오도록 하고 있다.

수정, 생성, 삭제 때는 조금 다른 점이 있다.

```js
const user = await User.findOne({});
const comment = await Comment.create();
await user.addComment(comment);
// 또는
await user.addComment(comment.id);
```

여러 개를 추가할 때는 배열로 추가할 수 있다.

```js
const user = await User.findOne({});
const comment1 = await Comment.create();
const comment2 = await Comment.create();
await user.addComment([comment1, comment2]);
```
관계 쿼리 메서드의 인수로 추가할 댓글 모델을 넣거나 댓글의 아이디를 넣으면 된다. 수정이나 삭제도 마찬가지이다.

### 7.6.4.2 SQL 쿼리하기

만약 시퀄라이즈의 쿼리를 사용하기 싫거나 어렵다면 직접 SQL문을 통해 쿼리를 할 수도 있다.

```js
const [result, metadata] = await sequelize.query('SELECT * FROM comments');
console.log(result);
```

## 7.6.5 쿼리 수행하기

쿼리로 CRUD 작업을 수행합니다. GET /로 접속했을 때의 라우터는 User.findAll 메서드로 모든 사용자를 찾은 후, sequelize.html을 렌더링할 때 결괏값인 users를 넣는다.

시퀄라이즈는 프로미스를 기본적으로 지원하므로 async/await과 try/catch문을 사용해서 각각 조회 성공 시와 실패 시의 정보를 얻을 수 있다. 이렇게 미리 데이터베이스에서 데이터를 조회한 후 템플릿 렌더링에 사용할 수 있다.

---

GET /users와 POST /users 주소로 요청이 들어올 때의 라우터이다. 각각 사용자를 조회하는 요청과 사용자를 등록하는 요청을 처리한다. GET /에서도 사용자 데이터를 조회했지만, GET /users에서는 데이터를 JSON 형식으로 반환한다는 거에 차이가 있다.

GET /users/:id/comments 라우터에는 findAll 메서드에 옵션이 추가되어 있다. req.params.id로 값을 가져올 수 있다 GET /users/1/comments라면 사용자 id가 1인 댓글을 불러온다. 조회된 댓글 객체에는 include로 넣어준 사용자 정보도 들어 있으므로 작성자의 이름이나 나이 등을 조회할 수 있다.

---

댓글에 관련된 CRUD 작업을 하는 라우터이다. POST /comments, PATCH /comments/:id, DELETE /comments/:id를 등록하였다.

* POST /comments 라우터는 댓글을 생성하는 라우터이다. commenter 속성에 사용자 아이디를 넣어 사용자와 댓글을 연결한다.

* PATCH /comments/:id와 DELETE /comments/:id 라우터는 각각 댓글을 수정, 삭제하는 라우터이다. 수정과 삭제에는 각각 update와 destroy 메서드를 사용한다.