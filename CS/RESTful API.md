# RESTful API

Representational State Transfer API

1. HTTP를 통해 SOAP나 쿠키를 통한 세션 트래킹같은 별도의 전송계층 없이 전송하기 위한 아주 간단한 인터페이스를 말한다.(프로토콜이 아니다)

2. 기존의 Web application이 Service 중심이었다면  Rest는 Resource중심이다.

3. Resource  중심으로 설계하며 CRUD에 해당하는 HTTP의 4가지 메소드( POST, GET, PUT, DELETE)를 이용한다. 



## 구성요소

- **자원(RESOURCE)** 

  자원에 대한 정의이다. HTTP URI 형태로 나타난다.

- **행위(Verb)** - HTTP METHOD

  자원에 대한 행위이다. HTTP Method ( REST에서는 CRUD에 대한 동작을 나타낸다. POST, GET, PUT, DELETE이 해당된다.)

- **표현(Representations)**

  자원의 행위에 대한 내용이다. HTTP Message Payload를 나타낸다.



## 특징

**1. 클라이언트 / 서버 구조**

\- 서버가 클라이언트의 정보로 부터 조금은 자유로워지는 구조이다. 클라이언트가 서버로 전송하는 데이터에 대한 의존성을 낮춰준다. 



**2. 무상태성(Stateless)**

\- 각 요청에 대한 컨텍스트가 서버에 저장되어서는 안된다. REST는 Resource 중심이기 때문에 서버는 API를  통해 동작을 이해 하고 Resource에 접근할 수  있다. API를 작성하는 방법에 대해서는 아래에서 다룰 것이다.   Client는 서버에게 자신을 표현(?) 할 수있는 별도의 정보를 전달해야 한다.(API key or Token 정보)

**3. 캐시 처리 가능(Cacheable)**

\- www에서와 같이 클라이언트는 응답을 캐싱할 수 있어야 한다. 캐싱처리가 잘되면 클리이언트 - 서버 간  상호작용을 부분적, 완전하게 제거하여 scalability와 성능을 향상시킨다. 



**4. 계층화(Layered System)**

\- 클라이언트는 보통 대상 서버에 직접 연결되어쓴지, 중간 서버를 통해 연결되었는지를 알 수 없다. 중간 서버는 로드 밸런싱 기능이나 공유 캐시 기능을 제공함으로써 시스템 규모 확장성을 향상시키는데 유용하다. 



**5. Code on demand**

\- Server 측에서 실행가능한 코드를 Client에게 전송해줌으로서, Client의 기능을 확장할 수 있다. 



**6. 자체 표현 구조(SELF-DESCRIPTIVNESS)**

\- 별도의 문서가 필요없다 왜냐면! API를 보고 다 알수있기 때문이다



## RESTful이 되기 위해

**1. 동사형 보다는 명사형을 추구하라.**

\- ex) /getCompany/mocam (x)



**2.명사의 단수형 보다는 복수형을 추구하라.**

\- ex) /companies/mocam (o)



**3. URL의 Depth는 level2 정도를 지향하라고 한다.** 

\- URL을 간단하고 직관적으로!

\- API를 보고 동작을 이해할 수 있게 작성

\- ex) /companies/mocam  <= 사실 작성자 말고(명사형이라 더 힘들다)는 이해하기 힘들꺼 같다.

\- 서브 URL을 이용하는 방법  <= 이부분에 대해서는 잘 모르겠으니 [여기](https://www.slideshare.net/Byungwook/rest-api-60505484)를 참고하세요 



**4. HTTP 응답코드**

\- 사실 각 유명한 회사마다 사용하는 응답코드에는 차이가 조금씩 있다고 합니다.

\- 권장하는 기본 Response Code 입니다. 

(1) 200 : Success

 (2) 400 : Bad-request

 (3) 401 : 인증 인가 실패

 (4) 404 : Resource not Found - 리소스 찾을 수 없음

( 5) 500 : Internal Error 



**5. HTTP Response Body** 

\- 에러처리에 관한 상세한 내용은 HTTP body를 통해 표현합니다.

\- 각 숫자 대역마다 Error Code의 범위를 미리 정해 놓습니다.

\- ex) 회원관련 에러 1000대, 상품관련 에러 2000대)





**6. 부분 응답(partial Response)**

\- 이 부분도 추가적인 공부가 필요하다.. 잘 모르겠다ㅜ.ㅜ

\- 검색 HTTP GET에 쿼리스트링을 이용한다.

\- ex) user/?name=dongsu&region=seoul&offest=20&limit=10 

\- HATEOS(HyperMedia as the Engine of application state) 하이퍼미디어의 특징을 이용하여 HTTP Link를 함께 리턴하는 것이다. 

예를 들어 페이징처리 외에도 자바스크립트 소스나, 이후 발생할 url 링크등을 함께 투척하는 경우를 말한다.





- REST는 기본적으로 웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하기 때문에 웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일이다.
  REST는 네트워크 상에서 Client와 Server 사이의 통신 방식 중 하나이다.
- HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고, HTTP Method(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미한다.
  - 즉, REST는 자원 기반의 구조(ROA, Resource Oriented Architecture) 설계의 중심에 Resource가 있고 HTTP Method를 통해 Resource를 처리하도록 설계된 아키텍쳐를 의미한다.
    웹 사이트의 이미지, 텍스트, DB 내용 등의 모든 자원에 고유한 ID인 HTTP URI를 부여한다.
    CRUD Operation
    Create : 생성(POST)
    Read : 조회(GET)
    Update : 수정(PUT)
    Delete : 삭제(DELETE)
    HEAD: header 정보 조회(HEAD)

