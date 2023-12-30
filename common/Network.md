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

<br>

---
2. **CORS란 무엇이고, 어떻게 구현할 수 있는지 최대한 자세하게 설명해주세요.**

- 답

<br>

---
3. **https://google.com을 입력했을 때 생기는 일에 대해 설명해주세요.**

- 답

<br>

---
4. **http1.1, 2.0, 3.0에 대해 각각 설명해주세요.**

- 답