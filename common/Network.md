1. **TCP와 UDP 각각의 개념을 설명하고, 둘의 차이를 비교해주세요.**

- 답 : TCP는 신뢰성있고 연결을 지향하는 연결 프로토콜입니다.
  신뢰적인 전송을 보장하기에 handshaking이라는 것을 합니다. 이러한 기능으로 인해 TCP의 속도는 느립니다.
  handshaking은 3-way handshaking과 4-way handshaking이 있는데 3-Way handshaking과정을 거쳐서 연결을하고 4-way handshaking 과정을 거쳐 연결을 해제합니다. 그 과정에서 높은 신뢰성을 보장하지만 비 연결성 프로토콜인 UDP보다는 속도가 느립니다. 신뢰성이 보장되는 서비스에 많이 쓰입니다.

      udp는 연결을 설정하고 해제하는 handshaking과정이 없습니다. 서로 다른 경로에서 패킷의 순서를 부여하거나 흐름제어를 하지않기때문에 속도가 빠르고 네트워크 부하가 적지만 데이터 전송의 신뢰성이 낮습니다. 연속성이 중요한 실시간 서비스에 많이쓰입니다.

      UDP와 TCP의 대표적인 차이로는
      신뢰성과 속도입니다.
      UDP는 신뢰성이 낮지만 속도가 빠르며
      TCP는 신뢰성이 높지만 속도가 느립니다.

    <br>
    
    1-1. **TCP 연결 과정인 3-way handshake, 4-way handshake란 무엇인지, 그리고 각 과정에서 왜 단계 차이가 발생하는지 설명해주세요.**
    
    - 3-Way Handshake 는 TCP의 접속,4-Way Handshake는 TCP의 접속 해제 과정입니다.
    각 단계 차이가 나는 이유는 client가 데이터 전송을 끝냈다는 신호를 보냈어도 서버에서는 아직 보낼 데이터가 남아있을 수 있기 때문에 처음에FIN에 대한 ACK만 보내고, 데이터를 모두 전송한 후에 한번더 FIN 메시지를 보내기 때문입니다.

<br>

---

2. **CORS란 무엇이고, 어떻게 구현할 수 있는지 최대한 자세하게 설명해주세요.**

- 답 : 자바스크립트 엔진은 SOP라는 같은 출처의 리소스만 받아오는 보안정책을 두고 있습니다. 하지만 같은 도메인이라도 출처가 다른 서버가 많아지면서 일부 다른 도메인이랑도 데이터를 주고받는걸 허용해주는 보안정책이 cors입니다.
  cors에는 여러 중요한 속성들이 있는데 대표적으로 Access-Control-Allow-Origin , Access-Control-Allow-Methods, Access-Control-Allow-Headers ,Access-Control-Allow-Credentials,Access-Control-Expose-Headers 등이 있습니다.
  순서대로 , 어떤 url, 메소드, 헤더,쿠키또는 어떤인증, 내가 줄 헤더를 허용한 것인지에 대한 속성입니다.
  node.js 기준으로

let corsData = {
origin: '\*',  
 credential: true, // 사용자 인증이 필요한 리소스(쿠키 등) 접근
header:{"GET","POST"} // 허용되는 메소드
}

app.use(cors(corsData))
처럼 미들웨어 cors정책을 추가하면 구현할 수 있습니다.

<br>

---

3. **https://google.com을 입력했을 때 생기는 일에 대해 설명해주세요.**

- 답 : 사용자가 https://google.com을 검색했을 때.
  DNS 서버에 https://google.com을 검색해서 그에 맞는 ip주소를 찾습니다.
  여기서 DNS란 사용자가 알아보기 쉽게 ip주소의 별명을 지어준 것입니다.
  원래의 ip는 198.201.321.. 이런식으로 되어있지만 일반 사용자가 그걸 외워서 치기에는 불편하기떄문에 https://google.com라는 별명을 지어줍니다.
  ip주소를 찾았다면 그 ip주소를 사용하여 TCP통신을 통해 해당 ip서버에 요청을 보냅니다.
  요청을 받은 서버 https://google.com는 요청 내용을 처리해 응답 메시지를 만듭니다.
  그 응답메시지 또한 TCP통신을 통해 다시 사용자에게 전달합니다.
  브라우저는 받은 응답메시지를 통해 웹페이지를 구성하고 브라우저 렌더링과정을 거쳐 사용자에게 화면을 보여줍니다.
  <br>

---

4. **http1.1, 2.0, 3.0에 대해 각각 설명해주세요.**

- 답: http 1.1는 단일 요청 연결을 재사용할 수 있도록 유지가 됩니다.
  그렇기때문에 모든 요청에 대해 비용이 많이 드는 3-Way-handshaking을 할 필요가 없어져 요청 지연시간이 줄어듭니다.

      http 2.0은 여러 요청 스트림을 보낼 수 있는 http stream이 도입되었습니다.

      http 3.0은 기본 전송 프로토콜로 TCP대신 UDP기반인 QUIC이라는 새로운 프로토콜을 사용합니다.
