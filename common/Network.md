1. **TCP와 UDP 각각의 개념을 설명하고, 둘의 차이를 비교해주세요.**

- 답 : TCP와 UDP는 데이터를 보내기 위해 사용하는 프로토콜입니다. 
TCP는 연결 지향 방식이고 UDP는 비연결형 프로토콜입니다. 그렇기 때문에 TCP는 신뢰성이 보장되고 UDP는 신뢰성이 보장되지 않습니다. 또한 속도 측면에서 UDP가 TCP에 비해 더 빠릅니다. 

    <br>
    
    1-1. **TCP 연결 과정인 3-way handshake, 4-way handshake란 무엇인지, 그리고 각 과정에서 왜 단계 차이가 발생하는지 설명해주세요.**
    
    - 답 : TCP는 3-way handshaking과정을 통해 연결을 설정하고 4-way handshaking을 통해 해제합니다. 즉, 3-way handshaking은 TCP의 접속 과정이고, 4-way handshaking은 TCP의 접속 해제 과정입니다. 

<br>

---
2. **CORS란 무엇이고, 어떻게 구현할 수 있는지 최대한 자세하게 설명해주세요.**

- 답 : 브라우저에서는 보안적인 이유로 cross-origin HTTP 요청들을 제한하기 때문에 cross-origin 요청을 하려면 서버의 동의가 필요합니다. 이때 허락을 구하고 수락/거절하는 매커니즘을 HTTP-header을 이용해서 하는 것을 CORS라고 합니다.
구현을 할 때는 클라이언트에서 Origin 필드를 추가하고, Fetch api를 cors mode(mode: 'cors')로 설정한 뒤 서버에서 응답 헤더에 Access-Control-Allow-Origin: ~~ 을 추가하면 된다

<br>

---
3. **https://google.com을 입력했을 때 생기는 일에 대해 설명해주세요.**

- 답 : 우선 도메인인 google.com을 DNS 서버에서 검색을 한 뒤 IP주소를 찾아 사용자가 입력한 URL 정보와 함께 전달합니다. (DNS query 전달) 그 후 전달받은 IP주소를 보고 웹 브라우저가 웹 서버에게 해당 웹 사이트에 맞는 정적파일(문서, html)을 요청하고, WAS와 데이터베이스에서 웹 페이지 작업을 처리합니다. 마지막으로 브라우저 렌더링 과정(Critical Rendering Path)을 통해 웹 브라우저에 출력됩니다.




<br>

---
4. **http1.1, 2.0, 3.0에 대해 각각 설명해주세요.**

- 답 : HTTP/1.1은 표준 프로토콜로 주로 사용됩니다. HTTP/2.0과 HTTP/3.0은 HTTP/1.1의 성능을 개선한 것 입니다. HTTP/2.0은 1.1에서 속도를 개선한 것이고, HTTP/3.0은 TCP가 아닌 UDP를 사용한 것 입니다.