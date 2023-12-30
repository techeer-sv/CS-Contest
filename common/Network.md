1. **TCP와 UDP 각각의 개념을 설명하고, 둘의 차이를 비교해주세요.**

- 답 : TCP is connection oriented, wheras UDP is connectionless. TCP is slower than UDP but TCP guarntees the transmission of data.

    <br>
    
    1-1. **TCP 연결 과정인 3-way handshake, 4-way handshake란 무엇인지, 그리고 각 과정에서 왜 단계 차이가 발생하는지 설명해주세요.**
    
    - 답요: 3 way handshake is the method in which TCP establishes a connection... it goes through SYN -> SYN-ACK -> ACK. 4 way handshake is used for terminating. It goes through FIN -> ACK -> FIN -> ACK.

<br>

---
2. **CORS란 무엇이고, 어떻게 구현할 수 있는지 최대한 자세하게 설명해주세요.**

- 답: CORS stands for Cross-Origin Resource Sharing which is an HTTP-header based mehcanism which allows the use of resources from a source with different origins, such as domain, scheme, or ports. It can be implemented in the server with setting such as Access-Control-Allow-Origin with desired domains or use a proxy to bypass cross origin restrictions.

<br>

---
3. **https://google.com을 입력했을 때 생기는 일에 대해 설명해주세요.**

- 답: 1. When google.com is searched, it is looked up on the DNS server for the corresponding IP address. 2. HTTPS connection is established (Handshake, SSL/TLS) using the IP address. 3. A request is made to the google server. 4. Google server receives the request and a response is sent from the google server to the user.

<br>

---
4. **http1.1, 2.0, 3.0에 대해 각각 설명해주세요.**

- 답: 1.1: "Keep Alive" Host header and consistent connections. PUT, PATCH, DELETE, CONNECT, TRACE, OPTIONS methods are available. 2.0: Multiplexing through stream is supported. 3.0: Transport layer changed from TCP+TLS to UDP+QUIC.