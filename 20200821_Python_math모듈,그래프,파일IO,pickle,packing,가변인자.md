



## math모듈

#### 사용법: `import math`

#### `math.pi` :pi값을 가져온다



## 그래프

```python

#pip install numpy         ->수치해석   #for mac:pip3 install
#pip install matplotlib    ->그래프

import random

import matplotlib.pyplot as plt
import numpy as np
from unicodedata import category


def plt01():
    x=np.arange(0,11)
    y=x
    
    plt.plot(x,y)
    plt.xlabel('x')
    plt.ylabel('y')
    plt.legend(['y=x'])
    plt.show()
    
def plt02():
    y=[random.randint(0,10)for i in range(10)]
    x=range(10)
    plt.bar(x,y)
    plt.xticks(range(11))
    plt.yticks(range(11))
    plt.show()
    
def plt03():
    data=[random.randint(100,1000) for i in range(4)]
    plt.pie(data)
    category=['first','second','third','fourth']
    plt.legend(category)
    plt.show()
    
       
if __name__=='__main__':
    #plt01()    #선그래프
    #plt02()     #막대그래프
    plt03()
    
```







#### :book:#파이썬에서는 return되는 타입이 없는데 return을 해주는데 값이 없어도 에러가 뜨지 않고 None만 뜨고 끝난다 

#### :book: 파이썬에서의 문자는 sequenceial한 객체이다 



## 파라미터 기본값 주기

>   파라미터에 기본값을 주면 값이 들어오지 않았을 때 기본값이 적용된다
>
>   ```python
>      def prn(quantity=0,change=0):
>          pass
>   ```





## 모듈 안에서 원하는 부분만 가져오는 법

```python
#math에서 pi만 가져온다.
from math import pi
```



## math의 pi사용하기

```python

#math라는 module을 가져온다.
#import math

#math에서 pi만 가져온다.
from math import pi ㅡ
  

def circle(r):
    # pi * r * r
    return pi*r*r

if __name__=='__main__':
    r=int(input('원의 반지름: '))
    print('반지름이 {} 인 원의 넓이는 {} 입니다.'.format(r,circle(r)))
```



## 막대그래프 , 선그래프 만들기 

``` python
#-*-coding:utf-8 -*-

#pip install numpy         ->수치해석   #for mac:pip3 install
#pip install matplotlib    ->그래프

import random

import matplotlib.pyplot as plt
import numpy as np
from unicodedata import category


def plt01():
    x=np.arange(0,11)
    y=x
    
    plt.plot(x,y)
    plt.xlabel('x')
    plt.ylabel('y')
    plt.legend(['y=x'])
    plt.show()
    
def plt02():
    y=[random.randint(0,10)for i in range(10)]
    x=range(10)
    plt.bar(x,y)
    plt.xticks(range(11))
    plt.yticks(range(11))
    plt.show()
    
def plt03():
    data=[random.randint(100,1000) for i in range(4)]
    plt.pie(data)
    category=['first','second','third','fourth']
    plt.legend(category)
    plt.show()
    
       
if __name__=='__main__':
    #plt01()    #선그래프
    #plt02()     #막대그래프
    plt03()
    
```





## 파일 입출력 (I/O)

### with as 구문 : 인터프리터가 자동으로 구문이 끝나면 close()해준다

```python
#test01.txt라는 파일을 작성한다 
file=open('test01.txt','w')
file.write('Hello,World!')
file.close()

'''
r:읽기
w:쓰기(기존 내용 덮어쓰기)
a:쓰기(기존 내용 이어서 쓰기)
x:새로운 파일 만들어서 쓰기(이미 파일이 있으면 에러)
t/b: text/binary(default : t)
'''
#읽기 예제 1
file =open('test01.txt','r')
a=file.read()
file.close()
print(a)

#읽기 예제 2(자동으로 close해준다는 차이점이 있다)
with open('test01.txt', 'r')as file:
    a=file.read()
    print(a)
     
#이어쓰기 예제
file=open('test01.txt','a')
file.writelines('\nHello,Python!')
file.close()

#바이너리 형태의 파일을 작성하는 예제

import pickle

score={'name':'kh','kor':100,'eng':99,'math':56}
with open('test02.txt','wb')as file:   #쓰긴 쓸건데 binary형식으로 쓸거야
    pickle.dump(score,file)    
    #결과 : ��* 이런식으로 나온다 

#바이너리 형태의 파일을 읽어오는 예제
import pickle
from com.test05.io01 import file
file=open('test02.txt','rb') #binary파일을 읽어올겁니다
score=pickle.load(file)
file.close()

print(score)

```



## pickle , unpickling

>   #### 모듈 임포트: `import pickle`
>
>   #### 모듈 기본 사용법
>
>   ```python
>   with open('파일명',파일모드)as 랴ㅣㄷ:
>   	pickle.dump(데이터변수,file)
>   ```
>
>   #### 공통
>
>   -   pickle로 데이터를 저장하거나 불러올때는 파일을 **<u>바이트형식</u>**으로 읽거나 써야한다(wb,rb)
>   -   wb로 데이터를 입력하는 경우 .bin확장자를 사용하는게 좋다 
>   -   모든 파이썬 데이터 객체를 저장하고 읽을 수 있다
>
>   #### pickle : 파이썬 객체 - > 파일 (직렬화)
>
>   -   파이썬 객체 계층 구조가 바이트 스트림으로 변환되는 절차
>   -   리스트나 클래스 같은 텍스트가 아닌 자료형을 파일로 저장하기 위하여 사용한다
>   -   pickle 모듈을 이용하면 원하는 데이터를 자료형의 변경없이 파일로 저장하여 그대로 로드할 수 있다.
>   -   
>
>   #### 일반적인 방법으로 데이터 입력
>
>   -   ```python
>       # 파일에 텍스트 입력하기
>       >>>text="hello world"
>       
>       >>>with open('hello.txt','w')as f:
>       	   f.write(text)
>       >>>cat hello.txt
>       #helloworld
>       
>       #파일에 리스트 입력하기 > TypeError 발생
>       >>>list=['a','b','c']
>       >>>with open('list.txt','w')as f:
>            fwrite(list)
>       #TypeError발생
>       
>       ```
>
>   #### pickle 모듈을 활용하여 데이터 입력 및 로드
>
>   -   ##### 입력
>
>       -   **`pickle.dump(data,file)`**
>
>           ```python
>           import pickle 
>           list = ['a','b','c']
>           with open('list.txt','wb')as f:
>           #pickle.dump(list,f)
>           ```
>
>           
>
>   -   ##### 로드
>
>       -   **`변수 = pickle.load(file)`**
>
>       -   한줄 씩 파일을 읽어오고 더이상 로드할 데이터가 없으면 EOFErrof발생
>
>       -   **pickle.load(파일) 을 통해서 파일 내용을 읽어오려면, pickle.dump를 사용해서 데이터를 입력한 파일이어야한다.**
>
>           ```python
>           with open('list.txt','rb')as f:
>                s
>           #data=pickle.load(f) #단 한줄씩 읽어옴
>           print(data)
>           #['a','b','c']
>           ```
>
>           
>
>       
>
>   
>
>   #### unpickle : 파일 - > 파이썬 객체 (역직렬화)
>
>   -   바이너리 파일이나 바이트열류 객체로 부터 바이트 스트림을 객체 계층 구조로 복원한다
>   -   pickling으로 작업 한 파일을 불러들여 출력하는 과정 
>
>   #### 예제 
>
>   ```python
>   import pickle
>   dir='c/window/dir_pro'
>   ver='2.0'
>   file_load='c:/program/en/en,exe'
>   user={'ankiwoong':1.0,'anjia':2.0}
>   
>   with open('dir,bin','wb')as file:
>        pickle.dump(dir )
>   ```











## packing , unpacking

-   ### 공통

    -   패킹시 **`*`**를 붙인 변수는 남은 요소 전체를 리스트에 담아 저장한다
    -   패킹을 이용하여 swap을 쉽게할 수 있다.

-   ### packing

>   하나의 변수에 여러가지의 값을 포장하는것을 말한다
>
>   ```python
>   >>> a = 1,'가','A'
>   >>> print(a)
>   (1, '가', 'A')
>   ```
>
>   

-   ### unpacking

>   여러가지의 값을 가진 하나의 변수를 여러변수로 나누는 것을 말한다
>
>   ```python
>   >>> i,j,k = a
>   >>> print(i,j,k)
>   1 가 A
>   ```
>
>   



## 가변인자(Variable parameter)

>   위치, 키워드 인자의 개수가 많아지거나 인자의 수가 미정일 경우 가변인자를 사용한다
>
>   위치인자와 키워드인자 모두 가변인자로 사용가능하다
>
>   가변 위치인자(*args)는 임의개수의 위치인자를 <u>tuple형태</u>의 변수로 저장한다.
>
>   가변 키워드인자(**kwargs)는 임의개수의 키워드인자를 <u>dictionary형태</u>
>
>   #### 가변인자의 형태 : `*args` ,` **kwargs`
>
>   #### 위치 인자(Positional parameter) 
>
>   -    일반적으로 선언하는 인자
>
>   #### 키워드 인자(Keyword parameter) 
>
>   -   인자 뒤에 **`param=default`**형태로 기본값을 선언해주면 입력값이 있을 땐 위치 인자로 처리되고 값이 없을 때 default값으로 처리된다 
>
>   #### :book: 위치 인자 뒤에 키워드 인자가 오도록 순서를 지켜야한다 

