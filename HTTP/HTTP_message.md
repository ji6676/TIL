# 메세지의 흐름
## HTTP 메시지

HTTP 애플리케이션 간에 주고 받는 데이터의 블록을 뜻함
Client, Server, Proxy 사이를 흐름

### 메시지 방향

1. 트랜잭션의 방향
- 인바운드 : 메시지 → 서버 (서버방향)
- 아웃바운드 : 메시지 → 클라이언트 (사용자 에이전트 방향)

### 메시지의 부분

HTTP 메시지는 단순한 데이터의 구조화된 블록
시작줄, 헤더블록, 본문으로 나뉨

1. 시작줄 : 무엇을 해야되는지 알려줌
2. 헤더블록 : 속성값을 갖고있음
3. 본문 : 데이터를 갖고있음, 없을 수 도 있음

시작줄과 헤더는 그냥 줄단위로 분리된 아스키 문자열

## 메시지 문법

---

### 요청 메시지

    <method> <request url> <version>
    <header>
    <entity>

### 응답 메시지

    <version> <status code> <reason-phase>
    <header>
    <entity>

메서드 : 클라이언트에서 서버가 리소스에 대해 수행해주길 바라는 동작 (GET, POST ...)

요청 URL : URL 경로 구성 

버전 : HTTP /<major>.<minor> HTTP의 버전을 뜻함 

상태코드 : 요청 중에 무엇이 일어났는지를 표현하는 3자리 정수 (200, 302, 404 ...)

사유구절 : 숫자로된 상태 코드의 의미를 사람이 이해할 수 있게 설명 해주는 짧은 문구

엔티티 본문 : 임의의 데이터 블록을 포함하며, 없을 수 도 있음 (CRLF로 끝남)

## 시작줄

---

요청 : 무엇을 해야되는지 알려줌

응답 : 무슨일이 일어났는지 알려줌

### 요청줄

메서드와 그 동작에 대한 대상을 지칭하는 요청 URL을 갖고 있음
HTTP버전의 값 또한 가지고 있음

### 응답줄

요청에 해당되는 수행결과에 대한 상태 정보, 결과데이터를 클라이언트에게 돌려줌
HTTP 버전, 상태코드, 사유구문을 포함함

### 메서드
종류                설명                                본문데이터
GET	     서버의 어떤 문서를 가져온다                    	N
HEAD	 서버에서 어떤 문서에 대한 헤더만 가져온다	         N
POST	 서버가 처리해야 할 데이터를 보낸다	                 Y
PUT	     서버에 요청 메세지의 본문을 요청한다	             Y
TRACE	 메시지가 프록시를 거쳐 서버에 도달하는 과정을 추적	  N
OPTIONS	 서버가 어떤 메서드를 수행 가능한지 확인	         N
DELETE	 서버에서 문서를 제거한다	                        N


### 상태코드

클라이언트에게 서버에서 무슨일이 일어났는지를 말해줌
응답 메시지의 시작줄에 담겨 반환 되며 , 숫자로된 코드, 문자열로 되어있는 메시지 모두 반 환 됨

응답코드    정의된 코드   설명
100-199	    100-101	    정보
200-299	    200-206	    성공
300-399	    300-305	    리다이렉션
400-499	    400-415	    클라이언트 에러
500-599	    500-505	    서버 에러