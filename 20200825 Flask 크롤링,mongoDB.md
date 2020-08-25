# 📗Project : Python03_flask ~ Python05_Web

<br><br>

# Python web

### django 

>   -   ##### python 기반 web application framework로 웹 개발을 하기 위한 여러가지 서비스를 갖추고 있고 가장 많이 사용되고 있다
>
>   -   ##### MVC기반 패턴대로 개발할 수 있도록 이미 구조화 되어 있어서 프레임워크 가이드 대로 하면 손쉽게 개발이 가능하다 
>
>   -   ##### Framework 자체적으로 설계한 개발 패턴에서 크게 벗아날 수 없는 구조이다.



### flask 

>   -   ##### Python의 Micro framework를 기반으로 단순하고 매우 가벼운 web framework이다.
>
>   -   ##### 완전 기본적인 것만 제공하기 때문에 하나하나 필요한 부분을 추가하면서 만들어 나가야 한다 ( =자유도가 높다)
>
>   -   ##### 내가원하는 입맛대로 만들 수 있는 프레임워크
>
>   -   ### 다운로드
>
>       -   cmd - pip install flask
>
>       -   ### Jinja2 (template)
>
>       -   ### MVT( Model View Template) != MVC
>

## jinja2

>   ##### Jinja2는 Python 웹 프레임워크인 Flask에 내장되어 있는 Template엔진으로 JSP의 문법이나 ES6의 template string과 비슷한 문법을 가지고 있다 .
>
>   -   ##### **<%%>**  /   {%%} : (자바) 파이썬내용이 들어간다 , if나 for같은 제어문
>
>   -   ##### **<%=%>**  /    {{}} : 변수나 표현식
>
>   -   **<u>들여쓰기를 사용하지 않고 {% endfor %}와 같이 닫아준다</u>**
>
>   https://jinja.palletsprojects.com/en/2.11.x/''

## MVT패턴

>   장고 프레임워크에서는 View를 Template,Controller는 View라고 표현하며 MVC를 MVT 패턴이라고 한다 . 모델은 데이터 베이스에 저장되는 데이터를 의마하는 것이고 , 템플릿은 자용자에게 보여지는 UI부분을, 뷰는 실질적으로 프로그램 로직이 동작하여 데이터를 가져오고 적절하게 처리한 결과를 템플릿에 전달하는 역활을 수행한다.
>
>   #### Model 
>
>   -   #####  MVC패턴의 Model과 마찬가지로 데이터 간의 인터페이스를 담당한다 , 데이터 처리 및 유효성 검사와 관련된 모든 항목이 포함된다
>
>   #### View:
>
>   -   ##### 프레임 워크에서 실제 브라우저에 보이는 프레젠테이션 로직을 처리하고 사용자에게 인터페이스를 제공하는 방법을 제어하는 곳이다. (MVC에서 View와 비슷하다)
>
>   #### Template
>
>   -   ##### MVC패턴에서 Controller와 비슷한 역할을 한다 . 따라서 모든 비즈니스 로직을 처리한다 또한 Model과 Templates간의 다리 역할을 하기도 한다.
>
>   Django에서의 MVT패턴은 일반적인 MVC패턴과 각각의 패턴이 하는일은 크게 차이가 없지만 **MVT패턴에서는 View에 프레젠테이션 로직이 아닌 비즈니스 로직을 포함시킨다** 또한 기존 **MVC에서 Controller에서 처리해야 했던 일부를 Django프레임 워크에서 자동적으로 해준다.**
>
>   

<br>

<br>

## __init__.py파일

-   파이썬에서 패키지를 읽어들일 때 가장먼저 읽어들이는 파일로 패키지와 관련된 초기화 처리를 이부분에서 수행한다 

-   이 파일이 존재하는 디렉터리는 패키지의 일부임을 알려주는 역할을 한다.

<br>

<br>



## SSR

>   (java,python,django)
>
>   server side rendering 의 약어로써 단어 그대로 서버에서 렌더링을 작업한다. 기존에 존재하던 방식으로 사용자가 웹페이지에 접근할 때 서버에 페이지에 대한 요청을 하며 서버에서는 html,view와 같은 리소스들을 어떻게 보여질지 해석하고 렌더링하여 사용자에게 반환한다

## CSR

>   client side rendering 의 약어로써 최초에 1번 서버에서 전체 페이지를 로딩하여 보여주고 이후에는 사용자의 요청이 올 때마다, 리소스를 서버에서 제공한 후 클라이언트가 해석하고 렌더링을 하는 방식이다. 여기에 Angular JSmBackbone JS같이 SPA 개발에 쉬운 JS 프레임 워크가 등장했고 여기에 점점 클라이언트가 무거워지자 다시 VIEW만 관리하자는 철학으로 React JS가 등장했다 
>
>   ### 특징
>
>   -   화면이 더 빠르게 보인다 
>
>   #### Single Page Application
>
>   -   CSR의 한 종류로 비동기로 응답받은 데이터를 한페이지에서 모두 처리해주는 것
>

<br>

<br>

### :book: html 주석안에 {%%} 같은건 쓰면 안된다 따로 동작하기 때문에

### :book: python이랑은mysql sqllite를 많이쓴다 

### :book: javascript 의 for in문은 json의 value값을 못 가져온다

<br>

<br>

## 이클립스 에서 python크롤링

### cros문제 해결

![image-20200825131628495](C:\Users\shm11\AppData\Roaming\Typora\typora-user-images\image-20200825131628495.png)

-   cmd - pip install flask_cors
-   서버에서는 정상적으로 응답하지만 브라우저에서 막는것이다

<br>

<br>

## MongDB설치

https://www.mongodb.com/try/download/community



## no-sql

#### 고정되지 않은 테이블 스키마

-   필요할 때 마다 필드를 추가/제거 가능-> 개발 속도 향상

#### 데이터 간의 관계를 정의하지 않는 데이터베이스

-   db > collection > document

####  분산형 구조 (대용량 데이터 저장 용이)

-     데이터가 넘어오면 데이터를 분산해서 저장한다
-   하나의 컴퓨터가 잘못되어도 문제되지않도록하기 위해서
-   sharding 지원(클라스터 데이터 상호 복제)



### :book: MongoDB설치시 

#### 설치과정

-   complete - 그대로간다 - **<u>Install MongoDB Compass체크 해제</u>(mongodb실행 관리 프로그램을 설치하는것이다)**

#### mongodb path설정

-   시스템 변수 - path - 새로만들기 - C:\Program Files\MongoDB\Server\4.4\bin (추가) 

#### 설치확인

-   C:\data\db폴더 만들기 
    -   cmd - "mongod"	(oracle11g xe)라고 생각하면된다
    -   cmd - 'mongo'      (sqlplus) 라고 생각하면된다



## 킬 때마다 cmd에서 확인하기 싫으니깐 service로 등록해 놓는다

-   mongod.exe --dbpath "c:\data\db" --serviceName MongoDB --serviceDisplayName MongoDB

    ​	(한줄에 써야한다)

-   cmd - net start MongoDB (MongoDB라는 이름으로 실행 )

-   cmd - mongo



## 윈도우 환경변수

#### 사용자변수

-   컴퓨터에 있는 각 계정에서 사용하는 변수, 해당 사용자의 계정으로 컴퓨터에 로그인 시에만 적용되는 변수

#### 시스템변수

-   시스템 전체에 적용되는 변수







mongoDB

crud, aggregation(mapreduce)



python + mongo



spring MVC



spring + mongo



+-------------------여기까지 배울거임

geoJson 

sharding ( 분산처리 )

