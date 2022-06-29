작성자: 이세경

## 🎯HTTP 프로토콜이란?

HTTP(Hypertext Transfer Protocol)은 통신 프로토콜이다.

`프로토콜` 이란? 상호 간ㅇ에 정의한 규칙을 의미하여 특정 기기 간에 데이터를 주고받기 위해 정의되었으며, 통신 프로토콜을 쉽게 풀어보면, “나는 이렇게 줄 테니 넌 이렇게 받고 난 너가 준거 그렇게 받을께"정도

웹에서는 브라우저와 서버 간에 데이터를 주고받기 위한 방식으로 HTTP프로토콜을 사용하고 있다.

## 🎯HTTP 프로토콜 특징
 
HTTP 프로토콜은 상태가 없는(stateless)프로토콜이다. 여기서 상태가 없다라는 말은 데이터를 주고 받기 위한 각각의 데이터 요청이 서로 독립적으로 관리가 된다는 말이다. 좀 더 쉽게 말해서 이전 데이터 요청과 다음 데이터 요청이 서로 관련이 없다는 말이다.

HTTP프로토콜은 일반적으로 TCP/IP 통신 위에서 동작하며 기본 포트는 80번 이다.

## 🎯HTTP Request & HTTP Response

HTTP프로토콜로 데이터를 주고받기 위해서는 아래와 같이 요청(Request)을 보내고 응답(Response)을 받아야한다.

![request-response.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/250df3aa-cb54-4a3a-9d0b-7b96ad754a4c/request-response.png)

`클라이언트란?` 요청을 보내는 쪽을 의미하며 일반적으로 웹 관점에서는 브라우저를 의미한다. 
`서버란?` 요청을 받는 쪽을 의미하며 일반적으로 데이터를 보내주는 원격지의 컴퓨터를 의미한다.

## 🎯URL (Uniform Resource Locators)

서버에 자원을 요청하기 위해 입력하는 영문 주소, 

✅  URL

[http://www.domain.com:1235/path/to/resource?a=b&x=y](http://www.domain.com:1235/path/to/resource?a=b&x=y) 

- http : protocol
- [www.domain.com](http://www.domain.com) : host , IP주소를 domain화함
- :1235 : port; 기본 80port
- /path/to/resource : resource path
- ?a=b&x=y : query

## 🎯HTTP 요청 메서드

URL을 이용하면 서버에 특정 데이터를 요청할 수 있다. 여기서 요청하는 데이터에 특정 동작을 수행하고 싶으면 어떻게 해야 하냐.. 바로 HTTP요청 메서드(Http Request Methods)를 이용한다.

일반적으로 HTTP요청 메서드는 HTTP Verbs라고도 불린다.

- GET : 존재하는 자원에 대한 **요청**
- POST : 새로운 자원을 **생성**
- PUT : 존재하는 자원에 대한 **변경**
- DELETE : 존재하는 자원에 대한 **삭제**

데이터에 대한 조회, 생성, 변경, 삭제 동작을 HTTP 요청 메서드로 정의할 수 있다. 

## 🎯HTTP 상태 코드

앞에서 살펴본 URL과 요청 메서드가 클라이언트에서 설정해야 할 정보라면 HTTP 상태 코드(HTTP status Code)는 서버에서 설정해주는 응답(Response)정보이다.

### 2xx - 성공 : 대부분 성공을 의미

- 200 : GET 요청에 대한 성공
- 204 : No Content. 성공했으나 응답 본문에 데이터가 없음
- 205 : Reset Content. 성공했으나 클라이언트의 화면을 새로 고침하도록 권고
- 206 : Partial Conent. 성공했으나 일부 범위의 데이터만 반환

### 3xx - 리다이렉션 : 클라이언트가 이전 주소로 데이터를 요청하여 서버에서 새 URL로 리다이렉트를 유도하는 경우

- 301 : Moved Permanently, 요청한 자원이 새 URL에 존재
- 303 : See other, 요청한 자원이 임시 주소에 존재
- 304 : Not Modified, 요청한 자원이 변경되지 않았으므로 클라이언트에서 캐싱된 자원을 사용하도록 권고. ETag와 같은 정보를 활용하여 변경 여부를 확인

### 4xx - 클라이언트 에러 : 유효하지 않은 자원을 요청했거나 요청이나 권한이 잘못된 경우 발생

- 400 : Bad Request, 잘못된 요청
- 401 : Unauthorized, 권한 없이 요청, Authorization 헤더가 잘못된 경우
- 403 : Forbidden, 서버에서 해당 자원에 대해 접근 금지
- 405 : Method Not Allowed, 허용되지 않은 요청 메서드
- 409 : Conflict, 최신 자원이 아닌데 업데이트하는 경우

### 5xx - 서버 에러  : 서버쪽에서 오류가 난 경우

- 501 : Not Implemented, 요청한 동작에 대해 서버가 수행할 수 없는 경우
- 503 : Service Unavaillable, 서버가 과부하 또는 유지 보수로 내려간 경우

즉, 클라이언트에서 URL + 요청메서드(HTTP Request)를 보내면, 서버에서 상태코드 + 응답 Body(HTTP Response)를 클라이언트로 보낸다.
