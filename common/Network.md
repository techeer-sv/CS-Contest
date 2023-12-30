1. **TCP와 UDP 각각의 개념을 설명하고, 둘의 차이를 비교해주세요.**

- 답 : TCP(Transmission Control Protocol)는 신뢰성 있는 통신을 하기 위한 통신 규약이다. UDP(User Datagram Protocol)는 신뢰성보다는 인터넷 통신의 기본적이고 핵심적인 기능을 중시한 통신규약이다.  
이 둘의 가장 큰 차이점은 신뢰성의 보장 유무이다. 먼저 UDP는 위에 서술한 바와 같이 인터넷 통신의 기본적인 기능에 충실하기 때문에 신뢰성을 보장하는 handshake과 같은 기술들이 포함되어 있지 않다. 그렇기 때문에 통신 중 segment가 중간에 유실되더라도 UDP는 이를 신경쓰지 않는다.  
반대로 TCP는 신뢰성 보장하기 위한 프로토콜이다. 이를 위해 3-way-handshake, 혼잡 제어 등의 기술이 포함되어 있다.


    <br>
    
    1-1. **TCP 연결 과정인 3-way handshake, 4-way handshake란 무엇인지, 그리고 각 과정에서 왜 단계 차이가 발생하는지 설명해주세요.**
    
    - 답: 3-way handshake란 client와 server 처음 연결이 수립될 때 일어나는 과정이다. 
    1. client가 server에게 연결 요청을 한다.
    2. server가 client에게 연결 요청을 수락하는 응답을 보낸다.
    3. client가 응답을 받고 마지막 syn 와 함께 데이터를 같이 server에 전송한다.

    4-way handshake란 client와 server의 연결이 종료될 때 일어나는 과정이다.
    1. client가 server에게 연결 종료 요청을 보낸다.
    2. server는 종료 요청을 받았다는 응답을 client에게 보낸다.
    3. server는 연결 종료 준비가 되었다는 신호를 client에게 전송한다.
    4. client는 이에 대한 응답을 server에게 전송하고 server는 응답을 받은 뒤에 연결을 완전히 종료한다.

    단계의 차이가 나는 이유는 4 way handshake에서 server가 연결 종료 준비가 완료되어 즉시 종료하게 된다면 종료하기 전에 client가 보내는 요청이나 응답은 정상적으로 server가 처리할 수 없게 된다. 그렇기 때문에 client가 마지막 요청 혹은 응답을 확인하기 위해 4 way handshake 과정을 수행하게 된다.

<br>

---
2. **CORS란 무엇이고, 어떻게 구현할 수 있는지 최대한 자세하게 설명해주세요.**

- 답: CORS(Cross-Origin Resource Sharing)이란 다른 출처의 리소스를 공유할 수 있도록 하는 보안 정책이다. 원칙적으로는 동일한 출처끼리만 공유가 가능하지만 선택적으로 다른 출처의 접근을 허용시킬 수 있다.  
 cors는 요청 헤더에 Origin과 그에 대한 응답 헤더에 Access-Control-Allow-Origin이 서로 일치하는지 확인하여 불일치 시 브라우저에서 cors 정책 위반으로 인해 접근이 불가능하다.

<br>

---
3. **https://google.com을 입력했을 때 생기는 일에 대해 설명해주세요.**

- 답
- http request를 보내기 전에 https://google.com의 DNS의 IP address가 필요하다.
- 이를 위해 DNS query를 보내기 위해서는 MAC address 또한 필요하다.
- MAC address를 알아내기 위해 ARP를 수행한다.
- ARP, DNS query 이후 DNS IP address로 요청을 보내야 한다.
- 이를 위해 TCP 연결을 수립한 후 HTTP GET 요청을 보낸다.
- DNS server는 그에 맞는 응답을 client에게 보낸다.

<br>

---
4. **http1.1, 2.0, 3.0에 대해 각각 설명해주세요.**

- 답