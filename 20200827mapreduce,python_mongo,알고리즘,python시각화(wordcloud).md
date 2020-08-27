# Python06프로젝트 , Python_Bonus프로젝트



## map reduce

복잡한 집계 작업에 소용된다 

javascript function을 사용하여 복잡한 작업처리 

순서 : query - map - reduce - out

map : 가져오는 것

reduce : 처리해주는 것

<br><br>

## 문제

#### test가 final인 document들의 이름과 국어와 영어를 출력하는데, '국어와 영어의 합'을 출력하자

```mysql
#map
function myMap(){
#score에서 값을 하나하나 가져와서 넣어준다, this가 score를 가리킨다
	emit(this.score,{name:this.name,kor:this.kor,eng:this.eng,test:this.test})
}
#reduce
#key,values값을 myMap으로부터 받아온다 
function myReduce(key,values){
	#
	var result={name:new Array(),kor:new Array(),eng:new Array(),total:new Array()};
	
	values.forEach(function(val){
		if(val.test=='final'){
		result.total+=val.kor+val.eng+" ";
			reuslt.name+=val.name+" ";
			result.kor+=val.kor+" ";
			result.eng+=val.eng+" ";
		}
	});
	return result;
}
-------------------------------------------
#map
function myMap(){
	emit(this.score,{name:this.name,kor:this.kor,eng:this.eng,test:this.test})
}

#승민이형 reduce ()
function myReduce(key,values){
   var result = {name: new Array(),kor:new Array(),eng:new Array(),total:new Array()};

   values.forEach(function(val){
   if(val.test=='final'){
   result.total+=val.kor+val.eng+" ";
   result.name+=val.name+" ";
   result.kor+=val.kor+" ";
   result.eng+=val.eng+" ";
   }
});
return result
}

#실행한 결과를 myRes라는 collection에 저장해준다 
#myMap에서 가져온 값들을 myReduce에 보내주는데 key값은 name value값은 this.name
db.score.mapReduce(myMap,myReduce,{out:{replace:'MyRes'}})

db.MyRes.find()
```

<br><br>

# Python Mongo

-   ###  cmd - pip install pymongo (다운로드)

-   ### PyMongo에 대한 모든것 : https://pymongo.readthedocs.io/en/stable/api/index.html

-   ### PyMongo Tutorial : https://pymongo.readthedocs.io/en/stable/tutorial.html

### pymongo설치

-   #### cmd - python - import pymongo  (pymongo 설치 확인)

#### pymongo API

-   #### pymongo - api reference - collection(우리가 쓰는게 collection이니깐 )



#### PyMongo 예제

```python
#-*-coding:utf-8 -*-

#MongoClient로 연결하기 
#PyMongo 로 작업 할 때의 첫 번째 단계 MongoClient는 실행중인 mongodb 인스턴스 를 만드는 것 입니다. 그렇게하는 것은 쉽습니다.
from pymongo import MongoClient 

#MongoDB와 연결
#client=MongoClient('qclass.iptiom.org',27017) #학원서버
client=MongoClient('127.0.0.1',27017)

#연결된 client에서 db와 연결(getting a database)
#db=client.test  #test데이터베이스 가져온다
db=client['test'] #위에랑 똑같다 

#연결된 db에서 collection가져오자(getting a collaction)
#collection=db.score
collection=db['score']  #위에랑 똑같다 

for doc in collection.find(): #collecation안에있는거 가져와서
    print(doc)

------------------------------------------------------------------------------------------------------------------------

#-*-coding:utf-8 -*-

from pymongo import MongoClient
#mongo_client랑 차이점
import pprint
from pydoc import doc

client=MongoClient('localhost',27017)
db=client.test
score=db.score   

cursor=score.find()
print(cursor)       #document들을 묶어놓은 객체를 Cursor라고 하고 하나씩 가지고 나올거다

for doc in cursor:
    pprint.pprint(doc) #pprint : (파이썬)이쁜출력
    
print('------')

lee=score.find({'name':'이순신'})      #find로 값일 가져오면 기본적으로 cursor객체 형태로 가져온다
print(lee)      #하나만 가져와도 cursor객체로 가져와지기 때문에 값이 제대로 나오지 않고 cursor값이 나온다 않는다
for doc in lee:
    print(doc)
    
print('-------')

hong=score.find_one({'name':'홍길동'}) #find_one으로 값을 가져오면 cursor객체가아닌 값 그대로를 가져와서 바로 출력해 줄 수 있다
pprint.pprint(hong)

print('------')
#국어점수가 60점보다 더 큰 document들을 모두 출력하자
kors=score.find({'kor':{'$gt':60}})
for e in kors:
    pprint.pprint(e)


print('---------')
#갯수구하는 함수
print('score collection 안에 있는 document의 총 갯수 : ' , score.count_documents({}))   
```





## (pymongo) insert_one ()  

-   리턴값:  **`InsertOneResult`**
    -   InsertOneResult : 방금 저장한 document의 _id값을 가진다

```python
res1=score.insert_one({'name':'성현모','kor':100,'eng':50,'math':90})
print(res1.inserted_id)  #결과값 : 5f472602fd7efe95030c47ff 
```



## (pymongo) insert_many([배열])

-   리턴값 : **`InsertManyResult`**  
    -   InsertManyResult  : 방금 저장한 document들의 object id값들을 가진다 

```python
res2=score.insert_many([{
        'name':'한지용',
        'kor':100,
        'eng':100,
        'math':100
    },
    {
        'name':'강여림',
        'kor':90,
        'eng':90,
        'math':90
    },
    {
        'name':'김지후',
        'kor':90,
        'eng':80,
        'math':90
    },
    {
        'name':'위영석',
        'kor':95,
        'eng':93,
        'math':90
    }
    ])
#inserted_ids   - s가 붙는다
print(res2.inserted_ids)
```



## (pymongo) update()

```python
#-*-coding:utf-8 -*-

from pymongo import MongoClient


client=MongoClient('localhost',27017)
db=client['test']
score=db['score']

#name이 자기이름인 document 하나를 찾아서, 국어점수를 0점으로 만들자.

res1=score.update_one({'name':'성현모'},{'$set':{'kor':0}}) #result값뭔지확인??
print(res1.matched_count)   #선택된 값의갯수
print(res1.modified_count) #변경된 값의갯수

print('-----')

res2=score.update_many({'eng':{'$lte':90}},{'$set':{'eng':0}})
print(res2.matched_count)
print(res2.modified_count)

res3=score.find()
for i in res3:
    print(i)
```

<br>

<br>

## (pymongo) delete()

```python
#-*-coding:utf-8 -*-

from pymongo import MongoClient

client=MongoClient('localhost',27017)
db=client.test
score=db.score


#name이 자기이름인 document 하나를 찾아서, 삭제하자.

#단일삭제
res1=score.delete_one({'name':'성현모'})
#결과값 확인?
print(res1.deleted_count)

#다중삭제
res2=score.delete_many({'math':{'$lt':100}})
#결과값 확인?
print(res2.deleted_count)

print('-----')

print(score.delete_many({}).deleted_count)	#조건이 없어서 전부 삭제된다
```

<br><br>

## (pymongo)aggregation

```python
#-*-coding:utf-8 -*-
from pymongo.mongo_client import MongoClient
from pymongo import MongoClient
import pprint

client=MongoClient('localhost',27017)
db=client.test
score=db.score

aggr=score.aggregate([
        {'$match':{'kor':{'$gte':90}}},
        {'$group':{'_id':'mysum','sum':{'$sum':'$kor'}}}
    ])

print(aggr) 
#결과 : <pymongo.command_cursor.CommandCursor object at 0x000002697CDA3220>
#CommandCursor:  iterate 한 객체 ( https://pymongo.readthedocs.io/en/stable/api/pymongo/command_cursor.html )

pprint.pprint(list(aggr))
```

<br><br>

## 알고리즘

### 버블정렬

```python
#-*-coding:utf-8 -*-
#버블정렬
def bubble(sort_data):
    ran=sort_data.__len__()
    for i in range(ran-1):
         for j in range(ran-1-i):
             if sort_data[j]>sort_data[j+1]:
                 sort_data[j],sort_data[j+1]=sort_data[j+1],sort_data[j]
             print(sort_data)
    
if __name__=='__main__':
    sort_data=[5,2,1,3,4]
    bubble(sort_data)
```

### 팩토리얼

```python
#-*-coding:utf-8 -*-


#n! = n*(n-1) * (n-2) * ... * 2 * 1

def factorial(n):
    res=n
    for i in range(1,n):
        print(i)
        res*=i
    return res

#재귀함수
def factorialRecursion(n):
    #종료 조건!!!
    if n==1:
        return 1
    return n*factorialRecursion(n-1)


if __name__=='__main__':
    n=int(input('input n: '))
    print('{} factorial= {}'.format(n,factorial(n)))
    print('{} factorial={}'.format(n,factorialRecursion(n)))
```





## word cloud

Python_Bonus - visual - cloud01.py 

-   #### cmd  -  pip install wordcloudd  (설치)

-   한글을 지원해주지 않는다 
-   json객체의 데이터를 원하는 글씨체 ,모양으로 만들어 파일을 만든다 

```python
#-*-coding:utf-8 -*-

#pip install wordcloud
from wordcloud import WordCloud
import json 
#크롤링 복붙해온다


cloud=WordCloud(font_path='Goyang.ttf',background_color='white',max_words=30,width=400,height=300)

with open('webtoons.json',encoding='utf-8') as file:
    webtoon = json.load(file)
    
res=dict()
for webtoon in webtoon['webtoons']:
    res[webtoon['title']]=int(float(webtoon['star'])*100)
    
visual=cloud.fit_words(res)
visual.to_image()
visual.to_file('cloud.png')
    
```





## Container

>   ##### OS와 비슷하지만 OS보다 가볍다

## OS

>   ##### 하드웨어와 소프트웨어 사이에서 소프트웨어가 잘 동작할 수 있도록 하드웨어를 움직여주는 소프트웨어





