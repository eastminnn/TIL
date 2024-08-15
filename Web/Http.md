# HTTP
HTTP (Hypertext Transfer Protocol) 는 웹 클라이언트와 웹 서버 간에 데이터를 주고받는데 사용되는 프로토콜이다.    

HTTP는 클라이언트 - 서버 모델을 기반으로 동작한다. 클라이언트가 HTTP Messages 양식에 맞춰 요청을 보내면, 서버도 HTTP Messages 양식에 맞춰 응답한다.

HTTP는 기본적으로 TCP/IP 프로토콜을 기반으로 동작한다. 클라이언트는 서버의 IP 주소와 포트 번호를 알고 있어야 하며, 이 정보를 사용하여 서버와 통신한다.

# HTTP 특징
### 무상태성 (Stateless)
HTTP는 상태를 유지하지 않는 Stateless 프로토콜이다. 즉 서버는 각각의 요청을 별개로 처리하며 이전 요청의 정보를 저장하지 않는다. 이는 서버의 부하를 줄이고 클라이언트와 서버 간의 통신을 단순화하여 처리 속도를 향상시킨다.

### 비연결성 (Connectionless)
HTTP는 Connectionless 프로토콜이다. 즉  요청과 응답이 한 번 이루어지면 연결을 끊는다. 이전 요청과 응답의 정보를 유지하지 않기 때문에 서버 부하를 줄일 수 있지만, 새로운 연결을 맺는 데 드는 시간이 추가로 발생할 수 있다.

### 클라이언트 서버 구조
HTTP는 Request / Response 구조로 통신한다. 클라이언트는 서버에 요청(Request)을 보내고, 서버는 클라이언트에게 응답(Response)을 보낸다. 이 요청과 응답은 HTTP 메세지라는 형식으로 주고 받는다.

![alt text](/Image/Web/HTTP1.png)

# HTTP Message
HTTP는  Request/Response 구조로 통신한다. 따라서 통신할 때 사용하는 메세지의 구조를 간략하게 살펴보자.

## Request Message
![alt text](/Image/Web/HTTP2.png)

### start line
HTTP Request Message의 시작 라인으로, 세 가지 부분으로 구성 되어있다.

- HTTP method : 요청의 의도를 담고 있다.
- Request target : HTTP Request가 전송되는 목표 주소이다.
- HTTP version : version에 따라 Request 메시지 구조나 데이터가 다를 수 있어서 version을 명시해야한다.

### headers
해당 request에 대한 추가 정보(addtional information)를 담고 있는 부분이다.

Header는 크게 네 종류로 나뉜다

- General header : 요청과 응답 모두에 적용되지만 바디에서 최종적으로 전송되는 데이터와는 관련이 없는 헤더
- Request header : 페치될 리소스나 클라이언트 자체에 대한 자세한 정보를 포함하는 헤더 (내가 보내는 메세지의 헤더)
- Response header : 위치 또는 서버 자체에 대한 정보(이름, 버전 등)와 같이 응답에 대한 부가적인 정보를 갖는 헤더 (내가 받은 메세지의 헤더)
- Entity header: 컨텐츠 길이나 MIME 타입과 같이 엔티티 바디에 대한 자세한 정보를 포함하는 헤더
>http://www.ktword.co.kr/test/view/view.php?m_temp1=5905

### body
HTTP Request가 전송하는 데이터를 담고 있는 부분으로, 전송하는 데이터가 없다면 body 부분은 비어있다. 보통 post 요청일 경우, HTML 폼 데이터가 포함되어 있다.

## Response Message
![alt text](/Image/Web/HTTP3.png)

### status line
HTTP Response의 상태를 간략하게 나타내주는 부분으로, HTTP Response의 status line은 3가지 부분으로 구성된다.

- HTTP version : version에 따라 Response 메시지 구조나 데이터가 다를 수 있어서 version을 명시해야한다.
- Status Code : Response의 상태 코드이다.
- Status Text

### headers
Request의 headers와 동일하다. 다만 response에서만 사용되는 header 값들이 있다. 예를 들어, User-Agent 대신에 Server 헤더가 사용된다.

### body
Response의 body와 일반적으로 동일하다. Request와 마찬가지로 모든 response가 body가 있지는 않다. 데이터를 전송할 필요가 없을 경우 body가 비어있게 된다.

# HTTP Method
HTTP 메서드는 클라이언트가 서버에게 요청을 보낼 때 사용되는 행동(action)을 정의하는 방법이다. HTTP 메서드는 요청 헤더(Request Header)에 포함되며, 서버는 이를 통해 클라이언트가 원하는 동작을 이해하고 요청을 처리한다.

주로 사용하는 HTTP 메서드는 다음과 같다.

### GET: 리소스 조회
- 서버에 전달하고 싶은 데이터는 query(쿼리 파라미터, 쿼리 스트링)를 통해서 전달
- 메시지 바디를 사용해서 데이터를 전달할 수 있지만, 지원하지 않는 곳이 많아서 권장하지 않음
> ex) 게시판 리스트 불러오기

### POST: 요청 데이터 처리(주로 등록에 사용)
- 메시지 바디를 통해 서버로 요청 데이터 전달
- 서버는 요청 데이터를 처리
- 메시지 바디를 통해 들어온 데이터를 처리하는 모든 기능을 수행한다.
- 주로 전달된 데이터로 신규 리소스 등록, 프로세스 처리에 사용
> ex) 회원가입 / 로그인

### PUT: 리소스를 대체(해당 리소스가 없으면 생성)
- 리소스가 있으면 대체하고, 없으면 생성(쉽게 이야기해서 덮어버림)
- 클라이언트가 리소스를 식별하여, 클라이언트가 리소스 위치를 알고 URI 지정한다. 이는 클라이언트가 리소스 위치를 모르는 POST 요청과의 차이점이다.
> ex) 회원정보 전체 수정

### PATCH: 리소스 부분 변경
- 리소스의 일부분을 변경한다.
- 변경 방식이 멱등이어도 되고, 멱등이 아니어도 된다.
> ex) 회원정보 일부 수정(update)

### DELETE: 리소스 삭제
- DELETE 메서드는 지정된 리소스를 삭제한다.
> ex) 회원정보 삭제

# HTTP Status code
상태 코드는 IETF (Internet Engineering Task Force)에서 정의한 인터넷 표준에 따라 개발되며, 다섯가지 클래스로 분류된다.

### 1xx: Informational - 요청 정보 처리 중
서버가 요청을 클라이언트에서 성공적으로 수신했으며 서버 끝에서 처리 중이라는 정보를 나타낸다. 서버의 임시 응답이며 일반적으로 상태 줄과 선택적 헤더 만 포함하며 빈 줄로 끝난다. 현재는 거의 사용하지 않는다.

### 2xx: Success - 요청을 정상적으로 처리함
서버가 요청을 받고 성공적으로 처리되었음을 나타낸다.

### 3xx: Redirection - 요청을 완료하기 위해 추가 동작 필요
브라우저는 자동으로 다른 URL로 리디렉션되므로 브라우저 창에는이 코드가 표시되지 않지만, 이미지 파일처럼 캐싱된 파일을 새로고침 후 확인하면 3xx 코드를 확인할 수 있다.

### 4xx: Client Error - 서버가 요청을 이해하지 못함
서버가 해결할 수 없는 클라이언트 측 에러 코드다. 주로 클라이언트(사용자)가 서버에 잘못된 요청을 했을 경우 발생한다.

### 5xx: Server Error - 서버가 요청 처리 실패함
서버가 클라이언트의 요청을 처리하지 못했을 때 발생한다. 서버는 보안 상 통신하지 않는 것이 가장 좋으므로 대부분의 에러 코드를 500 Error로 처리한다.

> https://hahahoho5915.tistory.com/62#Request%--Message