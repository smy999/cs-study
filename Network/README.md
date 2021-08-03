# Network

* [OSI 7계층](#OSI-7계층)
* [TCP/IP의 개념](#TCP/IP의-개념)
* [TCP와 UDP](#TCP와-UDP)
* [TCP와 UDP header 분석](#TCP와-UDP-header-분석)
* TCP의 3-way-handshake와 4-way-handshake
* HTTP와 HTTPS
* HTTP 요청/응답 헤더
* HTTP와 HTTPS 동작 과정
* CORS란

<br>

## OSI 7계층

**OSI(Open System Interconnect)** 는 세계표준화기구(ISO)가 제정한 것으로, **'어떤 경로와 방식으로 데이터가 송수신되는가'** 를 보여주는 **Network Model**이다.

초기 정리가 되지 못해 어지럽고 복잡했던 네트워크 장치로 인해 회사의 장비마다 호환이 되지 않는 어려움이 있었다. 이런 불편함을 해소하기 위해 네트워크를 7계층으로 분리하면서 OSI라는 표준을 만들었다.



#### 계층 분리를 왜하는가?

* 계층을 역할별로 분리하면서 문제 발생시 문제의 현상을 보았을 때 어떤 계층에 문제가 생겼는지도 파악이 가능하다.

#### header

* 각 계층은 하위계층을 사용하고 현계층의 기능을 포함하여 상위 계층에 제공한다. 그래서 계층구조는 위에서 바라보았을 때 아래층이 안보이는 구조라 볼 수 있다. 따라서 최상위 계층만 보면 그 아래계층을 모두 포함하고 있다.

<br>



![network_OSI_7layer](https://user-images.githubusercontent.com/33407191/127737230-5d52f1d3-1cbc-4e9c-b63f-1bac11376392.png)

<br>



### Physical Layer

* 하드웨어 전송 기술로, 전기적/기계적 신호를 주고받는 계층
* 상위 계층인 Data-Link Layer에서 형성된 data packet을 전기 신호나 광 신호로 바꾸어 송수신하는 역할
* data의 종류나 오류를 제어하지 않는다.
* 전송 단위: bits 0, 1
* 사용처: 통신 케이블, 허브, 리피터

<br>



### Data-Link Layer

* Point to Point 간의 신뢰성 있는 전송을 보장하기 위한 계층
* data packet을 형성하고 전송하는 것을 규정
* 전송 데이터에 대한 CRC 오류제어가 필요하다.
* 전송 단위: Frame
* 사용처: MAC Address, 스위치, 브릿지

<br>

### 

### Network Layer

*  IP주소를 제공하는 계층
* data에 목적지 주소를 지정하고 전송 경로를 결정하는 데 필요한 조건
* Node들을 거칠때마다 routing(라우터의 NAT 기능 활성화=공유기 역할)을 해주는 역할
  * 공유기는 하나의 외부 통신선에서 들어오는 요청을 사설망에 연결되어있는 컴퓨터에게 전달해주는 역할을 한다.
* 전송 단위: Packet
* 사용처: 라우터, L3 스위치, IP 공유기

<br>

### 

### Transport Layer

* End to End 사용자들이 data를 주고 받을 수 있게 하는 계층
* Protocol: TCP/UDP
* 전송 단위: Segment
* 사용처: TCP, UDP Protocol

<br>



### Session Layer

* Data를 만드는 계층
* 하위 계층과 상위 계층과의 연결(= 데이터와 서비스를 연결)
* LAN 사용자가 서버에 접속할 때 이를 관리하는 기능
* 전송 단위: data
* 사용처: RPC, Socket

<br>



### Presentation Layer

* Code 간의 번역을 담당하여 사용자 시스템에서 data의 형식상 차이를 다루는 부담을 응용 계층으로부터 덜어 주는 역할
* Data의 압축, 암호화, 복호화
* Application Layer에서 보내오는 data를 ASCII Code나 EBCDIC 등 기본코드로 포맷하는 기능
* 전송 단위: data
* 사용처: 데이터의 압축이나 인코딩

<br>



### Application Layer

* 응용 프로세스와 직접 관계하여 일반적인 응용 서비스를 수행하는 계층
* data를 처음으로 받는 계층
* Protocol: HTTP, FTP
* 전송 단위: data
* 사용처: 파일전송, 원격접속, 전자메일

<br>



### Capsulation

![network_OSI_capsulation](https://user-images.githubusercontent.com/33407191/127737235-dad2f853-87ed-4b74-963a-9c37805b645c.png)

* 송신자가 data를 보낼 때 처음 Application Layer에서 header를 붙여 하위 계층으로 넘겨줍니다. Presentation Layer은 Application Layer에서 내려온 header와 data를 하나의 data로 간주한다. 그래서 다시 자신의 header를 붙인다. 이런 과정은 __Encapsulation__이라고 한다.
* Data를 받은 수신자는 반대로 Physical Layer부터 시작해 header의 정보를 확인하고 떼어낸다. 그리고 난 후 상위 계층으로 data를 전달한다. 이렇게 header를 떼어내는 과정을 __Decapsulation__이라고 한다.

<br>

<br>



## TCP/IP의 개념

Data가 목적지에 전달될 수 있도록 보장해주는 통신 규약으로, TCP와 IP 두가지의 protocol로 구성된다.

컴퓨터가 통신할 때, 특정 규칙이나 protocol을 사용하여 순서대로 data를 전송 및 수신한다. 

전세계를 통해 가장 일상적으로 사용되는 프로토콜 세트 중 하나가 **TCP/IP(Transmission Control Protocol/Internet Protocol)**이다.

**TCP/IP**는 네트워크에 연결된 여러 컴퓨터(host) 사이의 통신을 허용한다. 각 네트워크는 해당 네트워크의 host와 통신하는 다른 네트워크에 연결될 수 있다. Packet 교환 및 Stream 전송으로 작동하는 많은 유형의 네트워크 기술이 있지만, **TCP/IP**는 하드웨어에 구애받지 않는다는 하나의 큰 장점이 있다.



![network_TCP_IP](https://user-images.githubusercontent.com/33407191/127740213-04753637-f4c9-4c10-9045-d21760a2ef78.png)

* IP
  * packet 전달 여뷰를 보증하지 않고, packet을 보낸 순서와 받는 순서가 다를 수 있다. __Unreliable Datagram Service__
* TCP
  * IP위에서 동작하는 protocol로 data의 전달을 보증하고 순서대로 받게 해준다.
* Internet Protocol Suit?
  * Internet에서 컴퓨터들이 서로 정보를 주고받는데 쓰이는 protocol의 모음이다. Internet protocol suit 중에서 TCP/IP가 가장 많이 쓰여서 TCP/IP suit라고 불리기도 한다.

<br>

<br>



## TCP와 UDP

Transport Layer는 송신자와 수신자를 연결하는 통신 서비스를 제공하는데, 이곳에서 사용되는 protocol에 대표적으로 TCP, UDP가 있다.

TCP는 internet 상에서 data를 메시지의 형태로 보내기 위해 IP 위에서 동작하는 연결형 protocol,

UDP는 data를 datagram 단위로 처리하는 비연결형 protocol

❕TCP와 UDP에 대한 자세한 설명은 더욱 구체적으로 공부하여 작성하겠습니다.❕

<br>

#### TCP?

TCP의 경우 **신뢰성**있는 통신을 보장한다. 따라서 데이터가 전달되는 과정에서 여러 스위치, 라우터을 거치면서 데이터가 잘못 전달되는 현상이나 전달이 안되는 경우 오류제어, 흐름제어를 통해 신뢰성있는 데이터가 전달될 수 있도록 한다. 또한, 연결 시 3-way hanshaking 방식으로 목적지와 상호 packet을 교환하여 연결한다. 연결을 종료할 때는 4-way hanshaking 방식을 사용한다. 신뢰성 연결과 전달을 보장하는 만큼 중간의 확인 과정을 거치고 연결을 계속 유지해야되기 때문에 그만큼의 자원이 더 들어간다.

<br>

#### UDP?

UDP은 비연결형 Protocol로, data를 **빠르게** 전달하는데에 초점을 두고 있다. 따라서 UDP는 목적지에 data가 제대로 전달 되었는지 조차 확인하지 않는다. 비연결을 지향하기 때문에 데이터를 전달 시 TCP에 비해 오버헤드가 적다. 그래서 신뢰성 있는 데이터 전송이 필요할 때보다 streaming같이 연속적인 특성을 가지고 있는 서비스에 사용한다.

<br>

#### Port Number?

TCP와 UDP는 **Port Numer** 라는 숫자를 이용하여 어떤 application에 data를 전달할지 식별한다. Port Number는 0~65535 범위를 가지며 범위에 따라 용도를 달리한다.

* 0~1023: **well-known-port**, web server와 mail server 등과 같이 **일반적인** server software가 client의 요청을 기다릴때 사용
* 1024~49151: **registered port**, 제조업제의 **독자적인** server software가 server software가 client의 요청을 기다릴때 사용
* 49152~65535: **dynamic port**, server가 client를 식별하기 위해 사용

<br>

### 공차

* 공통점
  * TCP와 UDP는 port number를 이용하여 주소를 지정하는 것과 data 오류검사를 위한 checksum이 존재한다.

* 차이점
  * 확실한 데이터 전송을 원하면(정확성)? TCP!
  * 빠른 데이터 전송을 원하면(신속성)? UDP!

| 구분                    | TCP                                 | UDP                  |
| ----------------------- | ----------------------------------- | -------------------- |
| 연결 방식               | 연결형                              | 비연결형             |
| 교환 방식(단위: Packet) | Byte Stream(연결형: 가상 회선 방식) | Datagram(비연결형)   |
| 순서 여부               | 순서 보장                           | 순서 미보장          |
| 수신 확신               | 수신 여부 확인                      | 수신 여부 미확인     |
| 통신 방식               | 일대일                              | 일대일/일대다/다대다 |
| 신뢰 보장               | 신뢰 보장                           | 신뢰 미보장          |
| 속도 비교               | 느림                                | 빠름                 |
| Header 크기             | 최소 20byte                         | 고정 8byte           |

<br>

<br>



## TCP와 UDP header 분석



![network_TCP_header](https://user-images.githubusercontent.com/33407191/127744422-5d1c9d12-b335-4627-a2f4-6adec072dcf3.png)

* Source Port : 출발 Port Number로, 응용 프로그램 별로 port number가 정해저 있는 것도 있지만, 대부분 송신측에서 임의의 번호를 사용
* Destonation Port : 목적지 Port Number로, 응용 프로그램에 따라 정해져 있다.
* Sequence Number : 송신측에서 지정하는 순서 번호, 전송되는 byte를 기준으로 증가
  * SYN = 1 : 초기 sequence number,  Acknowledgement number는 이 값에 1을 더한 값
  * SYN = 0 : 현재 session의 이 segment data의 최초 byte 값의 누적 sequence number

* Acknowledgement number(응답 번호) : 수신측 프로세스가 제대로 수신한 byte를 응답하기 위해 사용

* Data Offset : TCP segment의 시작 위치를 기준으로 data의 시작 위치를 표현(TCP header의 size)

* Reserved : 지금 사용하지 않지만 나중을 위해 예약해 놓은 field로, 0으로 채워진다.

* Flags(제어 bits) : SYN, ACK, FIN등의 제어 번호

* Window Size : 수신 window의 buffer size를 지정할 때 사용, 0이면 송신 프로세스의 전송을 중지

* Checksum : TCP segment에 포함되는 protocol header와 data에 대한 오류를 검출할 때 사용(= header와 data 오류를 확인하기 위한 field)

* Urgent Pointer(긴급 위치) : 긴급 data를 처리하기 위함, URG flag bit가 지정된 경우에만 유효
* Option : 최대 segment size 지정 들 추가적인 사항이 있을 때 사용



<br>



![network_UDP_header](https://user-images.githubusercontent.com/33407191/127744423-4889a6ef-3206-43d7-9125-c5f19b7ac4b1.png)

* Source Port : 출발 Port Number로, 응용 프로그램 별로 port number가 정해저 있는 것도 있지만, 대부분 송신측에서 임의의 번호를 사용
* Destonation Port : 목적지 Port Number로, 응용 프로그램에 따라 정해짐
* Checksum : header와 data 오류를 확인하기 위한 field로, UDP header는 오류 복구를 위한 field가 불필요하기 때문에 TCP header에 비해 간단

<br>

<br>



## 참고자료

OSI 7계층

* https://velog.io/@dyllis/OSI-7%EA%B3%84%EC%B8%B5-%EC%A0%95%EB%A6%AC
* http://www.tibs.co.kr/network/3/osi72.htm
* https://reakwon.tistory.com/59
* https://faq.hostway.co.kr/index.php?mid=Linux_ETC&page=16&document_srl=1434&m=0



TCP/IP의 개념

* https://www.ibm.com/docs/ko/aix/7.1?topic=management-transmission-control-protocolinternet-protocol
* https://velog.io/@rosewwross/TCPIP
* https://aws-hyoh.tistory.com/entry/TCPIP-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0
* https://ko.wikipedia.org/wiki/%EC%9D%B8%ED%84%B0%EB%84%B7_%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C_%EC%8A%A4%EC%9C%84%ED%8A%B8



TCP와 UDP

* https://mangkyu.tistory.com/15
* https://coding-factory.tistory.com/614



TCP와 UDP Header 분석

* https://m.blog.naver.com/PostView.nhn?isHttpsRedirect=true&blogId=minki0127&logNo=220804490550
* https://websecurity.tistory.com/92
* https://www.netmanias.com/ko/post/blog/5372/ethernet-ip-ip-routing-network-protocol/packet-header-ethernet-ip-tcp-ip
