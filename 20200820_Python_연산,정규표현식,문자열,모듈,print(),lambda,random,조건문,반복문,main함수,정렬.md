# 복습

#### [] : list : 순서있음 중복 가능 

#### {}: set,dictionary

#### () : tuple





# Python

#### :book: eval함수는 보안적으로 매우 위험하다 (경로)

#### :book:언어마다 정규식이 조금씩 다를 수 있기 때문에 사용전에 확인해야한다 

#### :book: python에서는 스네이크 기법을 주로 쓴다.

#### :book: 문자와 숫자를 동시에 쓰려면 +가 아닌 ,(콤마)를 써야한다 

#### :book:#python 에는 ++가 없다!!!!!!!!!!!!!!!!!!!!!

#### :book:python은 리턴값이 2개이상일 수 있다

#### :book:None == null

#### :book: java1.8의 특징이 lambda이다. :star:

#### :book:Python은 인터프리터 언어이기 때문에 main메서드가 밑으로 와야한다 :star:



 



## Python 연산

### 산술연산

```python
a=21
b=2
print(a+b)
print(a-b)
print(a*b)
print(a**b) # a의 b제곱
print(a/b) #실수값 몫
print(a//b) #나누고 나머지 제거 : 몫(floor division)
print(a%b) #나머지(modulo)
```

### 비교연산

```python
a,b=3,5
print(a==b)
print(a!=b)
print(a>b)
print(a<=b)
print(a is b)	#같다
print(a is not b)	#같지않다

print(True or False) #True
print(False and True) #False
print(not False) #True
```

### 범위연산:star:

```python
lst=list(range(100)) #0~99
print(lst) #전부출력
print(lst[2]) #3번째 출력
#[start : end] -> start~end-1
#[start : end : step ] -> start~end-1까지 step만큼씩 증가
print(lst[12:49])# 12~48 까지 출력
print(lst[12:49:3])#12~48 까지 3씩증가
```



### :star:문자열도 순서가 있기 때문에 index로 찍을 수 있다.

```python
str01='Hello World!'
print(str01)
print(str01[6:11])
```

### reverse (뒤에서부터 출력)

```python
str01="Hello world"
str01[-1]) #!
str01[=1: ]) #!  # 진행방향은 그대로인 것 같다
str01[:-1]) # Hello World #-1번지 직전까지
str01[::-1] #뒤에서부터 하나씩 출력해준다 #!dlroW olle
```

### 멤버연산 (in , not in)

```python
lst02=[0,1,2,3,4,5]
print(3 in lst02) #True
print(5 not in lst02) #False
print(7 not in lst02) #True
```









## 정규표현식 (re)

>   #### 정규식 도움 사이트 : https://regexr.com/
>
>   -   #### `import re` : 정규표현식을 사용하기위한 모듈
>
>   -   ### match()
>
>       -   원본 문자열의 시작부분부터 패턴과 매칭이 되는지 검사한다 , 문자열 중간에 찾을 패턴이 있더라도 시작부터 패턴이 일치하지 않으면 찾지 못한다 
>
>   -   ### group()
>
>       -   (정규표현식)이렇게 그룹으로 묶어 반환된 Match object객체에서 값을 얻어오는 메서드
>       -   원하는 구릅위 값만 가져올 수도 있다.
>
>   -   ### search()
>
>       -   이 메서드는 처음부터 검사해 나가지만 매칭되는 패턴을 찾으면 더이상 검사하지 않는다
>
>   ```python
>   '''
>   Regular Expression
>   
>   . : 문자 1개
>   ^ : 문자열 시작
>   $ : 문자열의 마지막
>   [] : 문자 집합
>   | : or
>   () : 괄호 안 정규식 그룹
>   
>   * : 0 or more
>   + : 1 or more
>   ? : 0 or 1
>   {n} : n번 반복
>   {n,m} : n번부터 m번
>   {n , } : n번부터 무한대
>   '''
>   """
>   
>   r : 문자열 표기법 (re 모듈의 확장 문법)
>   \w : [a-zA-Z0-9_] : a~z A~Z 0~9_ 까지 전부 다 포함한다는 의미이다.
>   \W : [^a-zA-Z0-9] : 위의 문자를 제외한 나머지 문자
>   \d : [0-9] : 0~9까지를 의미한다
>   \D : [^0-9] : 해당 숫자를 제외한 나머지 문자
>   \s : [\t\n\r\f\v] : (공백문자) 탭, 줄바꿈 , 처음으로 , 활성 위치를 다음 페이지의 시작으로 , 활성 위치를 수직 탭의 위치로 옮김
>   \S : [^\t\n\r\f\v] : 공백을 제외한 나머지 문자
>   \b : 단어의 시작과 끝의 빈 공백
>   \B : 단어의 시작과 끝이 아닌 빈 공백
>   \\ : \(역슬래시)
>   \[n] : 지정된 n만큼 일치하는 문자열 
>   \A : 문자열의 시작 = \s안의(\r)이랑 같다
>   \Z : 문자열의 끝
>   """
>   
>   #예제
>   
>   str01= '나의 이메일은  kh.123@kh.com123 입니다.'
>   match= re.search(r'[\w]*.[\w]*@[\w]*.[a-zA-Z]*',str01)  #문자들이 여러개 들어갈거야 0또는 그이상으로 , @가 들어가고 ,a~z,A~Z,. 이 갯수상관없이 들어감 
>   print(match.group()) # MatchObject 객체로부터 실제 결과 문자열을 얻기 위해서는 group() 메서드를 사용한다.
>   ```
>
>   



## module(모듈)

>   함수를 배포하면 모듈이 된다.



## split()

>   문자열의 값을 원하는 문자로 잘라서 list의 형태로 return 해준다 
>
>   원하는 개수만큼만 자를 수도 있다.
>
>   ### split예제
>
>   ```python
>   #split
>   str01='Hello, World!\nHello, Python!'
>   print(str01)
>   
>   arr01=str01.split(' ')
>   print(arr01)        #list로 return 된다
>   
>   arr02=str01.split(' ',1) #'공백 1개를 자를거다'라는 의미이다 , 결과:['Hello,', 'World!\nHello, Python!']
>   print(arr02)
>   
>   arr03= re.split("[\s]\[,]",str01)
>   print(arr03)
>   ```



## join()

>   iterable한 객체에 원하는 문자를 추가해서 하나의 문자열로 반환한다
>
>   ### join예제
>
>   ```python
>   arr04=['1','2','3','4']
>   print(arr04)
>   a = '+'.join(arr04)
>   print(a)
>   #결과 : 1+2+3+4
>   ```







## 문자 줄바꿈 없이 출력하는 방법

```python
	print('문자or숫자...', end=' ')
```





## format()

#### print('{ } * { } = { }'.format( i , j , i*j ))



## for문 숫자 거꾸로 출력하기

```python
for i in range(10,0,-1):
    print(i,end=' ')
```



##   print()함수

>   #### **`print('i',i,seq='=',end=' ')`**
>
>   -   ###### **end** 인자를 사용하면 print함수 마지막 효과를 변경할 수 있다 (기본값 : 개행)
>
>   -   ###### **sep** 인자를 사용하면 콤마로 구분된 문자열을 다르게 결합할 수 있다 (기본값 : 공백)
>
>   -   ###### **file** 인자를 사용하면 출력 결과를 파일, 표준에러처리로 보낼 수 있다
>
>   -   ###### %기호를 활용하여 변수값을 출력할 수 있다(오래된 방식)
>
>       -   ###### (%d정수, %f 실수, %s 문자열)

### 

## format()함수

```python
        print('커피 {}잔이 나왔습니다 \n잔돈은 {}원 입니다...'.format(quantity, change))
```



## lambda함수

>   ##### 함수를 미리 만들지 않고, 필요할 때 바디를 만들어서 사용한다 
>
>   -   #### lambda 사용할변수 : 식(파라미터)
>
>   -   #### 람다식안에 람다식도 사용가능하다
>
>   -   #### 람다식 파라미터 주는법
>
>       -   ```python
>           (람다식)(파라미터)
>           ```
>
>   -   #### lambda 예제
>
>   ```python
>   
>   # lamda function : 익명함수 (거의맞음)-> 함수를 만들지 않고, 필요할 때 바디를 만들어서 사용한다(자바)
>   
>   hap01= lambda a,b : a+b
>   print(hap01(10,20))
>   
>   god=lambda a,b:a*b
>   print(god(30,40))
>   
>   hap02=lambda a,b,c:a+b+c
>   print(hap02(5,6,7))
>   
>   #람다
>   a=[(1, 'one' ,9) , (2,'tow',8),(3,'three',7),(4,'four',6)]
>   print(a)
>   a.sort(key=lambda a:a[1])  #a의 key로 정렬해달라는 의미
>   print(a)
>   
>   #★람다에 파라미터주는법 1
>   min01=(lambda x,y: x if x<y else y)(11,22)  # x  if 조건 else y  :   x가 작은게 참이면 x 거짓이면 y
>   print(min01)
>   
>   #람다
>   #  x랑 y랑 입력하여, x가 y보다 크면 x , 아니면 y 리턴
>   max01=lambda x,y: x if x>y else y
>   print(max01(33,44))         #★람다에 파라미터주는법 2
>   
>   
>   b=lambda x: (lambda y:x+y)                  #★람다안에 람다 넣는법
>   c=b(100) #lambda y : 100 + y
>   d=c(90) #100+90
>   print(d)
>   print(b(100)(90))  # d
>   
>   
>   
>   #1~100 사이의 숫자 중 5의 배수를 출력하자
>   e= lambda x:bool(x%5)  #5의 배수일때만 false가 나타난다 따단
>   five=[i for i in range(1,101) if not (1)]
>   print(five)
>   #None == null 
>   # f=lambda x: x if(x % 5 !=0) else None
>   # result = [i for i in range(1,101) if not f(i)]
>   
>   result=[i for i in range(1,101) if not (lambda x: x if(x%5!=0) else None)(i)]       
>                                                                             
>   print(result)
>   ```



## random모듈

>   -   #### 사용법 : `import random`
>
>   -   #### random.randint(n,m) : n~m중에 하나의 숫자를 반환한다
>
>   -   #### random.random() : 0과1사이의 숫자를 반환한다.
>
>   ```python
>   #1부터 45 사이의 숫자 6개를 중복 없이 만들어서 리스트로 리턴하는 lotto() 함수를 만들자
>   #main함수에서 호출하여 출력하자
>   
>   import random
>   
>   def lotto():
>       lotto=set()
>       
>       while len(lotto)<=6:
>           ran=random.randint(1,45)
>           lotto.add(ran)
>       
>       result=sorted(lotto)
>       print(result)
>       return result
>       
>       
>   if __name__=='__main__':
>       print(lotto())
>   
>   #파이썬에서는 return되는 타입이 없는데 return을 해주는데 값이 없어도 에러가 뜨지
>   ```



## 조건문

### if , elif , else

### 조건문 예제

```python
b=2
if b==1:
    print('b==1')
elif b == 2:
    print('b==2')
else:
    print('b != 1 & b != 2')
```



## 반복문

### while 조건 :

>   ##### python에서는 while문에 else를 사용할 수 있는데 <u>정상적으로 완전히 종료되어야지만 else: 문이 실행</u> 된다
>

```python
i=1
while i<=10:
    if i>5:
        break
    print(i,end=' ')
    i+=1
else:
    print('i',i,sep='=')
  
print()

for i in range(1,11):
    if i%2==0:
        continue
    print(i,end=' ')
else:
    print('i',i,sep='=')
```

### for i in range(시작,끝-1) :

```python
subject= ['java' , 'javascript','python']

for i in subject:
    print(i,end=' ') #java의 print과 같이 옆으로 출력된다
else:           #python에서는 반복문에도 else를 붙일 수 있다 , 반복문이 끝나고 마지막에 실행된다
    print('재밌다')

for i in range(1,100):
    print(i,end="+")
    
print('\n구구단')

for i in range(2,10):
    print("\n")
    print("<<",i,"단>>")
    for j in range(1,10):
        #print(str(i)+'*'+str(j)+'='+str(i*j))
        #print(i,'x',j,'=',i*j)
        print('{}*{}={}'.format(i,j,i*j))
          
for i in range(10,0,-1):
    print(i,end=' ')
```



## Pass키워드

>   ##### 함수에 내용이 없을 때 에러발생을 막아준다 

```python
def gugu():
	pass
```





## print 함수에 변수값넣는법

1.  ### print ('<<%d단>>' %i)

2.  ### print('{} * {}={}'.format(i,j,i*j))

3.  ### print('<<', x , '단>>')    





## main함수

```python
	if __name__=="__main__":
		#내용
```



## input() 함수

해당 문자열을 보여주고 문자열을 입력받는다 

```python
n=input('dan : ')
```



## sort() sorted()함수

>   https://docs.python.org/3.8/library/stdtypes.html#list
>
>   #### sort()
>
>   -   리스트를 정렬된 상태로 변경한다
>   -   list만 사용가능하다
>
>   #### sorted()
>
>   -   이터러블 객체로부터 정렬된 리스트를 생성한다
>   -   어떠한 이터러블 객체도 사용가능하다
>
>   #### ket 매개변수
>
>   객체의 데이터 중에서 특정한 데이터를 기준으로 정렬하기 위해 key매개변수로 정렬을 하기 전에 각 요소에 대하여 적용되는 함수를 지정할 수 있다
>
>   ```python
>   >>>students =[
>   	('홍길동',3.9,2016303),
>   	('김철수',3.0,2016302),
>   	('최자영',4.3,2016301),
>   ]
>   >>>sorted(students, key= lambda student : student[2])
>   [('최자영',4.3,2016301),('김철수',3.0,2016302),('홍길동',3.9,2016303)]
>   ```
>
>   #### 오름차순 내림차순
>
>   list.sort()와 내장함수 sorted()는 모두 **reverse 매개변수**를 받는다 .**reverse 변수는 부울형으로 True 이면 내림차순이 된다**
>
>   ```python
>   >>> sorted(students, key=lambda student: student[2], reverse=True)
>   [('홍길동', 3.9, 2016303), ('김철수', 3.0, 2016302), ('최자영', 4.3, 2016301)]
>   ```
>
>   







