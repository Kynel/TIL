## REST = Representational State Transfer
### 정의
- 자원의 표현에 의한 상태 전달
  - 자원: 해당 소프트웨어가 관리하는 모든 것
    - ex) 문서, 그림, 데이터, 소프트웨어 자체 등등
  - 자원의 표현: 자원을 표현하기 위한 이름
    - ex) 학생 -> student
  - 상태 전달: 데이터가 요청된 시점에서 자원의 상태/정보 (JSON, XML, text...)
  
### 개념
- HTTP URI를 통해 자원을 명시
- HTTP Method(POST, GET, PUT, DELETE, PATCH)를 통해 해당 자원에 대한 CRUD Operation을 적용
  - 웹의 이미지, 텍스트 DB내용 등 모든 자원에 고유한 ID인 HTTP URI를 부여

### 장점
- HTTP 프로토콜의 인프라를 그대로 사용 -> 모든 플랫폼에서 사용 가능
- REST API 메세지가 의도하는 바를 명확하게 나타냄
- 서버와 클라이언트의 역할을 명확하게 분리

### 단점
- 표준이 존재하지 않음
- 사용할 수 있는 메소드가 4가지 밖에 없음 -> HTTP Method 형태가 제한적
- 구형 브라우저가 아직 제대로 지원해주지 않음
  - PUT, DELETE 사용?
  - pushState 지원X
  
### 기본 규칙
- resource
  - 동사보다는 명사, 대문자보다는 소문자 사용
  - `GET /Member/1` -> `GET /members/1`
- 행위
  - HTTP Method로 표현
  - URI에 HTTP Method가 들어가면 안됨
  - `GET /members/delete/1` -> `DELETE /members/1`

### 특징
- Uniform Interface(일관된 인터페이스)
  - URI에 대한 요청을 통일시키는 아키텍처 스타일
  - 사용자의 플랫폼, 언어, 기술에 무관
- Stateless(무상태성)
  - 이전 요청이 다음 요청에 연관되어서는 안됨
- Cachable(캐시 가능)
  - 웹의 기존 인프라 그대로 활용 가능
- Client-Server Architecture(서버-클라이언트 구조)
- Self-Descriptiveness(자체 표현)
  - 요청 메세지를 보고, 요청과 응답에 대한 파악 가능
- Layered System(계층 구조)

### HATEOAS
`Hypermedia As The Engine of Application State`
잘 지켜지지 않는 RESTful 의 조건
- Hypermedia(링크)를 통해서 애플리케이션의 상태 전이가 가능해야 함
- Hypermedia(링크)에 자기 자신에 대한 정보가 담겨야 함

ex) `GET https://my-server.com/article` 에 요청을 보냈을 때
해당 요청의 사용자가 할 '다음 행동'에 대한 정보가 응답에 포함되어야 함
```
{
  "data": {
    "id": 1000,
    "name": "게시글 1",
    "content": "HAL JSON을 이용한 예시 JSON",
    "self": "http://localhost:8080/api/article/1000", // 현재 api 주소
    "profile": "http://localhost:8080/docs#query-article", // 해당 api의 문서
    "next": "http://localhost:8080/api/article/1001", // 다음 article을 조회하는 URI
    "comment": "http://localhost:8080/api/article/comment", // article의 댓글 달기
    "save": "http://localhost:8080/api/feed/article/1000", // article을 내 피드로 저장
  },
}
```
HAL JSON을 활용해서 완벽한 구현이 가능

### HAL
`Hypertext Application Language`
JSON, XML 코드 내의 외부 리소스에 대한 링크를 추가하기 위한 특별한 데이터 타입

두 개의 타입
1. application/hal+json
2. application/hal+xml

리소스와 링크
- 리소스: 일반적인 data 필드
- 링크: 하이퍼미디어로 보통 _self 필드로 사요ㅗㅇ

```
{
  "data": { // HAL JSON의 리소스 필드
    "id": 1000,
    "name": "게시글 1",
    "content": "HAL JSON을 이용한 예시 JSON"
  },
  "_links": { // HAL JSON의 링크 필드
    "self": {
      "href": "http://localhost:8080/api/article/1000" // 현재 api 주소
    },
    "profile": {
      "href": "http://localhost:8080/docs#query-article" // 해당 api의 문서
    },
    "next": {
      "href": "http://localhost:8080/api/article/1001" // article 의 다음 api 주소
    },
    "prev": {
      "href": "http://localhost:8080/api/article/999" // article의 이전 api 주소
    }
  }
}
```
--------
출처
https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html
https://mangkyu.tistory.com/46
https://wonit.tistory.com/454
https://www.youtube.com/watch?v=RP_f5dMoHFc&ab_channel=naverd2
