# JSON vs javascript

유사한 구조를 갖지만 다른 개념!

- ### JS Object

  JS Engine 메모리 안에 있는 데이터 구조

- ### JSON

  객체의 내용을 기술하기 위한 text 파일

  - 파일이기에 확장자 명이 `.json` 파일 존재

---

- JS는 JSON을 Object로 쉽게 파싱할 수 있도록 `JSON.parse()` 메소드가 존재한다.
  - HTTP에서 메시지를 문자열로 전송하기 때문에 전송할 때 `JSON.stringify()` 메소드를 호출하여 JSON을 문자열로 만든다.
  - 데이터를 받으면 다시 JSON으로 변환하기 위해 `JSON.parse()` 메소드가 호출되고 이 데이터를 JS Object의 값으로 할당하면 Object가 된다.
- JS Object로 HTTP 통신하는 것이 아니라 JSON으로 서버와 클라이언트가 데이터를 주고 받는다.
  - object의 키값에는 "" 안붙이지만 JSON일 경우 postman에 데이터를 보낼 때 키에 ""을 붙인 이유!!!! (차이에 대한 이유)