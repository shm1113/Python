# MongoDB





## NoSQL

>   Document-Oriented(문서지향적) NoSQL데이터베이스이다. 어픈 소스이며 엔진은 C++로 작성되었다.
>
>   NoSQL이란 Not Only SQL의 약자로서 기존의 RDBMS(관계형 데이터베이스)의 한계를 극복하기 위한 새로운 형태의 데이터베이스이다.

interactive : 대화 형 함수 

REPL 대화형 양방향 쉘 

### REPL?

### mongo shell 

-   interactive javascript interface 
    -   interactive : 대화형 함수 
-   javascript interpreter를 사용한다 (javascript기반이다)
-   js program , library, fumction 활용가능



## mongoDB사용

#### cmd - use test (DB시작)

#### 

#### DB값입력

db.jstest.insert({name: ' mongo' , age :100 , class: 'qclass '}) : 값입력

db.jstest.insert({name'kh',class:'qclass})

### :book:DB에 들어가는 값의 형태가 달라도 상관이 없다.

### :book: nosql은 스키마가 없다 !!!!!!!!!!!!!!!:star:

### :book:스키마가 없기 때문에 제약조건도 없다?????

#### DB값확인

db.jstest.find()  :db의 값을 확인



var cursor = db.jstest.find() 

cursor =>find결과 출력

-   cursor라는 변수는 1회용이다 



var today=new Date()

today  => 날짜출력



### Mongo 안에 Database안에 Collection 안에 document가 있는 형태이다 

-   DB는 oracle과 같다 
-   데이터베이스 하나당 하나의 파일로 만들어져서 독립되어 있다.
-   예약된 DB
    -   admin : roog db
    -   local 복제되지 않는 db(특정 서버에만 저장하는 collection에 사용)
    -   config : shard 정보 저장

![image-20200826092745535](C:\Users\shm11\AppData\Roaming\Typora\typora-user-images\image-20200826092745535.png)



### Database

>   Database는 Collection들의 물리적인 컨테이너이다 
>
>   -   ##### Database는 0개 이상의 Collection들의 집합으로 구성되며 Collection은 0개 이상의 Document로 구성되고 Document는 1개 이상의 field로 구성된다

<br>

### collection

>   Collection은 RDMS의 table과 유사한 개념으로 Document들의 집합으로 구성된다
>
>   #### collection확인하는법
>
>   -   show collections

<br>

### Document

>   Document는 RDMS의 record와 유사한 개념으로 JSON objects 형태의 key - value의 쌍으로 이루어진 데이터 구조로 구성된다. 
>
>   -    {' field (KEY) ',' VALUE '}의 형태
>   -   data recode를 **<u>BSON(Binary JSON)으로 저장한다</u>** 
>       -   http://bsonspec.org/	(BSON)
>   -   banary형태(01010101) 이기 떄문에 가볍다
>   -   대소문자를 구별한다 
>   -   field(key) 중복 불가
>   -   Document는 **`_id`**라는 고유한 값을 갖는다 (시간/머신ID/프로세스ID/순차번호로 구성됨)

<br>

### jstest 

-   #####  mongo에서 자동으로 만들어지는 collections이다 

-   ##### DB에 저정되어서 사라지지 않는다 

<br><br>

## 스키마

>   ##### 스키마는 데이터베이스의 구조와 제약 조건에 관한 전반적인 명세를 기술한 메타데이터의 집합이다
>
>   ##### 스키마는 데이터베이스를 구성하는 데이터 개체(Entity) , 속성 (Attribute) , 관계(Relationship) 및 데이터 조작 시 데이터 값들이 갖는 제약 조건 등에 관해 전반적으로 정의한다 

<br><br>

## 기본 명령어

```mysql
show dbs : 전체database목록
db : 현재 사용중인 database확인
db.stats() : 데이터베이스 상태확인
```

<br>

<br>

## Mongo사이트

##### Mongodb.com - Docs - Server  : mongodb 매뉴얼  ( https://docs.mongodb.com/manual/ )

##### **MongoDB 명령어 사용법 mongodb Shell관련내용  :** https://docs.mongodb.com/manual/mongo/

##### **MongoDB CRUD 사용법 :** https://docs.mongodb.com/manual/crud/

### :book:mongodb는 레퍼런스 설명이 잘되어 있어서 공부할 때 참고하자

##### 





# MongoDB CRUD



## insert문

#### :book:그냥 insert()은 예전 것이기 때문에 잘 확인해야한다

### insertOne()

```mysql
db.qclass.insertOne(
	{
		name:'sung-hm',
		class:'qclass',
		kor:100,
		eng:94,
		math:96
	}
)
```

#### 변수에 값 담아서 insert하기

```mysql
> var lee={name:'lee-ss',midterm:{kor:'100',eng:'50',math:'70'}}
> db.qclass.insertOne(lee);
{
        "acknowledged" : true,
        "insertedId" : ObjectId("5f45bdfc96f75d7afec1bc13")
}
```



### insertMany()

```
db.qclass.insertMany([{name: '한지용', kor: 100, eng: 100, math:100}, {name:'황인규', kor:90, eng: 90, math: 90}, {name:'위영석', kor:80, eng:80, math:80}])
```



## _id 값

### ★insert할 때 _id라는 걸 따로 지정해주지않으면 mongoDB가 자동으로 만들어준다 

-   **_id** **(primary key) :** **명시하지** **않으면** **자동****으로** **ObjectId값** **생성** = rowid와같은놈 

-   ##### _id는 중복이 안된다 .

-   ##### 해당 document를 유일하게 식별해주는 식별자이다

![image-20200826100945848](C:\Users\shm11\AppData\Roaming\Typora\typora-user-images\image-20200826100945848.png)







#### :book: 싱클쿼터더블쿼터구분없다

#### :book: ket값에는 싱글쿼터를 안줘도 되는데 value값에는 문자열일 경우 반드시 넣어줘야한다 

#### :book: 0은 false 나머진 true로 잡힌다 





## nosql과 관계형 데이터베이스???의 차이

#### oracle은 데이터를 관리(추가,수정,삭제) 하기 위한것이면 noSQL은 대용량의 데이터를 수집해서 저장하고 싶은것이다

#### nosql은 저장형태가 지정되어 있지 않기 때문에 저장하기 좋다

#### 주로 BigData에 사용된다







## find()

https://docs.mongodb.com/manual/reference/operator/query/ (quert종류)

https://docs.mongodb.com/manual/tutorial/query-documents/#read-operations-query-argument (query 사용법)

![image-20200826103040033](C:\Users\shm11\AppData\Roaming\Typora\typora-user-images\image-20200826103040033.png)

collection : 어떤 collection이냐

query criterial : 어떤 조건이냐 ???

-   ```mysql
    db.qclass.find( { kor:100 } )
    ```

-   ```mysql
    db.qclass.find( { kor:{ $gte : 70} } )
    ```

projection :  1은 true이므로 값을 보여준다 

#### 특정 값만 가져오는법 

```mysql
db.qclass.find({kor:{$gte:70}},{name:1})

#_id출력되지 않게하기
db.qclass.find({kor:{$gte:70}},{_id:0,name:1})
```





## cursor

-   사용하는이유 : ??
-   한번 사용하고 사라진다
-   hasnext(),foreach(),toarray()등을 사용하여 cursor 내부의 document들을 사용할 수 있다.

```mysql
var cursor=db.qclass.find()
#find()를통해 리턴되는 cursor를 var 변수(js)에 저장할 수 있다
cursor.toArray()
#toArray()??????
```





## 문제

1.  #### where class='qclass'출력

```
db.qclass.find({class:'qclass'})
```



1.  #### midterm exists출력

```
db.qclass.find({midterm:{$exists.true}})
```



1.  #### 40<= kor < 90 출력

```
db.qclass:find({kor:{$gte:40,$lt:90}})
```







## 연산자 사용법 : {< field > : { < opr> : < value > }}



```mysql
db.qclass.find({name:/l/}) #l이 들어가는 것을 찾아준다

SELECT * FROM QCLASS WHERE NAME LIKE %L%
```

#### 정렬

```mysql
db.qclass.find(),sort({name:1})
#name의 오름차순으로 정렬된다
db.qclass.find(),sort({name:-1})
#name의 내림차순으로 정렬된다
db.qclass.find().sort({kor:-1}).limit(2)
#내림차순에서 높은에들 2개만 출력해라
db.qclass.find().sort({kor:-1}).skip(1)
#하나를 생략하고 출력해라
```





## update()??

document의 field를 수정한다

db.collection.update

1.  filter : 수정할 document를 find()
2.  update: 수정할 내용

### updateOne()

-   하나의 결과값만 수정된다

    ```mysql
    #name이 hong-gd인 애를 찾아서 '홍길동'으로 바꾼다
    db.qclass.updateOne(
    	{name:'hong-gd'},
    	{$set:{name:'홍길동'}}
    )
    ```

    

### updateMany

-   일치하는 모든 값이 수정된다

### replaceOne()

-   document자체를 바꿔버린다

```mysql
#class값만 남고 전부 사라진다
db.qclass.replaceOne({name:'홍길동'},{class:'bye'})
```



#### :book: 여러개를 update하려면 updateMany를 써줘야한다

## 함수처럼 사용하기

```mysql
 function updateKor(){
 var tmp= db.qclass.updateMany({kor:{$lte:90}},{$set:{kor:0}})
 return tmp
}
#한줄에 쓰면 인식을 못하므로 ;세미콜론을 찍어준다

```





## DELETE()

### db.qclass.deleteOne()

-   하나의 document 만 삭제한다

### db.qclass.deleteMany()

-   db.qclass.deleteMany({}) : 전부 다 삭제된다 
-   db.qclass.deleteMany({ 조건 }) :특정 애들만 삭제

## 문제

-   #### class라는 field가 존재하는 모든 document를 삭제하자 

```mysql
db.qclass.deleteMany({class:{$exists:true}})
```



### pretty() : 정렬된 형태로 출력해준다 





## 문제

-   #### midterm 필드 안에 kor 필드가 100인 document 찾아서 삭제하자 

    ```mysql
     db.qclass.deleteOne({'midterm.kor':{$eq:'100'}})
     # midterm.kor 에서 ''(퉈터)를 해주지 않으면 에러가난다 ( javascript변수로 인식해서 )
    ```

    



## 배열

```mysql
db.myfriends.insert({
		name:'아이언맨',
		buddy:['토르','헐크','호크아이']
	})
db.myfriends.insert({
	name:'슈퍼맨',
	buddy:['배트맨','원더우먼','아쿠아맨','조커']
})


```





## 문제

#### 참고

Query and Projection Operatiors (https://docs.mongodb.com/manual/reference/operator/query/)

update Operators  https://docs.mongodb.com/manual/reference/operator/update/ 

1.  #### 아이언맨의 친구에[캡틴아메리카,블랙위도우] 추가하자

    ```mysql
    db.myfriends.update(
    {name:'아이언맨'},
    {$push:{buddy:{$each:['캡틴아메리카','블랙위도우']}}
    })
    ```

    

2.  #### 2.슈퍼맨의 친구에서 가장 마지막 한명(조커) 빼자.

    ```
    db.myfriends.update(
    {name:'슈퍼맨'},{$pop:{buddy:1}}
    )
    ```

    

    

    ### ??each는 왜써줄까 ??



## inventory문제

### 준비물

```mysql
db.inventory.insertOne(
   { item: "canvas", qty: 100, tags: ["cotton"], size: { h: 28, w: 35.5, uom: "cm" } }
)

db.inventory.insertMany([
   { item: "journal", qty: 25, tags: ["blank", "red"], size: { h: 14, w: 21, uom: "cm" } },
   { item: "mat", qty: 85, tags: ["gray"], size: { h: 27.9, w: 35.5, uom: "cm" } },
   { item: "mousepad", qty: 25, tags: ["gel", "blue"], size: { h: 19, w: 22.85, uom: "cm" } }
])

db.inventory.insertMany( [
   { item: "canvas", qty: 100, size: { h: 28, w: 35.5, uom: "cm" }, status: "A" },
   { item: "journal", qty: 25, size: { h: 14, w: 21, uom: "cm" }, status: "A" },
   { item: "mat", qty: 85, size: { h: 27.9, w: 35.5, uom: "cm" }, status: "A" },
   { item: "mousepad", qty: 25, size: { h: 19, w: 22.85, uom: "cm" }, status: "P" },
   { item: "notebook", qty: 50, size: { h: 8.5, w: 11, uom: "in" }, status: "P" },
   { item: "paper", qty: 100, size: { h: 8.5, w: 11, uom: "in" }, status: "D" },
   { item: "planner", qty: 75, size: { h: 22.85, w: 30, uom: "cm" }, status: "D" },
   { item: "postcard", qty: 45, size: { h: 10, w: 15.25, uom: "cm" }, status: "A" },
   { item: "sketchbook", qty: 80, size: { h: 14, w: 21, uom: "cm" }, status: "A" },
   { item: "sketch pad", qty: 95, size: { h: 22.85, w: 30.5, uom: "cm" }, status: "A" }
] );
```

### 문제

1.  h가 20이상 w가25 이하인 물품을 출력하세요
2.  item값에 'p'를 포함한 제품을 출력하세요
3.  status가 없는 제품들만 출력하세요
4.  qty가 50이하인 제품들의 qty의 값을 100으로 바꿔주세요
5.  tags명이 있는 제품들만 출력하세요









## aggregation

-   collection이 각 stage를 거치면서 document 처리 및 집계

-   각각의 stage를 거치면서 집계가 된다

-   https://docs.mongodb.com/manual/aggregation/

-   ##### stage 순서가 중요하다:star:

-   #### pipeline

    -    이전 단계의 연산 결과를 다음 단계에서 사용

-   #### match stage

    -   $match를 사용해서 조건에 맞는 애들만 찾아서 다음 stage로 넘긴다

-   #### group stage

    -   $group을 사용해서 그룹핑시켜서 Results를 반환한다
    -   $cust_id : id가 cust_id인 애들을 참조해오겠다는 의미

-   #### 사용법

    ```mysql
    db.orders.aggregate([
       { $match: { status: "A" } },
       { $group: { _id: "$cust_id", total: { $sum: "$amount" } } }
    ])
    #orders라는 곳의 첫번째 스테이지에서 match를 status가 A인 애들만 가지고 다음 stage로 넘어간다
    두번쨰 stage에서는 $group를 사용해서 넘어온 결과값들을 group으로
    cust_id라는 값으로  group by를 해준다
    
    #stage 1 에서  status가 A인 값들을 가져온다  = stage1의 결과 
    #stage 2(=stage1의결과값을 가지고 시작) 에서 $cust_id라는 애를 참조해서  groupby 해줄것이다 , 나가면서 total컬럼에 $amount라는 값을 참조해서 $sum해주고 결과값을 반환한다 
    
    SELECT CUST_ID,SUM(AMOUNT)
    FROM ORDERS
    WHERE STATUS = 'A'
    GROUP BY CUST_ID  
    
    ```



-   ### 연습문제

```mysql
db.score.aggregate(
	{$match:{kor:{$gte:80}}},
	{$project: { kor: 1 }}	#select 보여주려는 결과컬럼
     {$group: {_id:'test',average:{$avg:'$kor'}}}	#_id 는 test라는
)

db.score.aggregate(
	{$match:{kor:{$gte:80}}},
	{$project: { kor: 1 }},	
     {$group: {_id:'test',average:{$avg:'$kor'}}}	
)	
# 결과 : { "_id" : "test", "average" : 92.5 }


#순서 바꿔봄
db.score.aggregate(
{$project: { kor: 1 }},	
{$match:{kor:{$gte:80}}},
{$group: {_id:'test',average:{$avg:'$kor'}}}
)
#결과는 같다 


```

## aggregate도전문제

-   ### test 가  midterm 인 document들 중 국어 점수랑 test만 가져와서 국어점수의 평균을 test라는 이름으로 출력하자( _id의 이름은 test의 값들로 한다. -> midterm / final)

```mysql
db.score.aggregate(
{$match:{test:'midterm'}},
{$project:{kor:1,test:1}},
{$group:{_id:'$test',average:{$avg:'$kor'}}}
)
```

### :star: '$이름' 으로 참조할 때 $project로 select한 애들중에서만 참조가 가능하다

### :star: $project를 하지 않으면 필드가 전체 선택된다









![image-20200826141523556](C:\Users\shm11\AppData\Roaming\Typora\typora-user-images\image-20200826141523556.png)

## map reduce :star::star: (빅 데이터에서 매우 중요)

-   aggregation framework가 처리하지 못하는 복잡한 집계 작업에 사용
-   javascript function을 사용하여 복잡한 작업 처리
-   shard에 대응 -> 분산처리가능 
-   각각의 분산저장된 

### 순서

-   query -> map -> reduce ->out                     
-   map : 어떤걸 가져올거고
-   reduce : 가져온걸 어떻게 처리해줄거고
-   out: 결과값을 출력해줄거야