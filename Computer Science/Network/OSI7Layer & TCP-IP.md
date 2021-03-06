### TCP/IP
---
#### `데이터`의 기술적 개념 
- 우선 데이터의 기술적 개념부터 생각해보자. 우리가 흔히 말하는 컴퓨터 화면을 통해 볼 수 있는 모든 데이터는 컴퓨터 밖 세상의 것들과 크게 다르지 않다.
- 책처럼 읽을 수 있는 인터넷 신문기사의 글자들, 눈으로 본 것과 똑같이 찍혀 sns에 업로드 된 사진들.. 이런 것들을 우리는 데이터라고 부른다. 너무 당연하게 받아들여온 개념이여서 일까? 우리는 그것이 수많은 0과 1로 이루어진 숫자에 불과하다는 사실을 쉽게 잊는다. 그래서 데이터가 어떻게 전달되는가? 를 생각해보자니 너무 막연하고 어렵게 느껴지는 것이다.
- 데이터는 `0` 혹은 `1` 로 이루어진 `숫자`이고, 컴퓨터는 이진법의 숫자를 전기의 `켜짐`과 `꺼짐`으로 표현할 수 있다. 즉, 데이터는 아주 긴 `전기 신호` 인 것이다. 이렇게 이해하니 막연했던 데이터 전달 과정을 조금은 상상할 수 있을 것 같다. 아주 긴 케이블이 필요하겠구나. 그런데 케이블만 있으면 정말 데이터를 전달할 수 있을까? 
  

#### 프로토콜(Protocol)이 필요하다.
- 컴퓨터, ip 폰 등 한 클라이언트에서 발생한 `데이터`가 상대방 컴퓨터 혹은 서버로 전달되기 위해서는 표준화 된 어떠한 약속 혹은 절차를 따라야한다. 전기신호가 그냥 케이블을 타고 상대방 컴퓨터로 전달되는 것이 아니다. 
- 보내는 쪽에서는 데이터를 안전하고 정확하고 신속하게 `규격화` 즉 포장하는 방법이 필요하고, 받는 쪽에서는 그 데이터를 안전하고 정확하고 신속하게 해석하는 방법이 필요한 것이다. 
- 그런 기술적 약속을 `프로토콜`이라고 한다. 네트워크를 공부한다는 것은 많은 프로토콜을 학습한다는 것과 마찬가지이다.
- 컴퓨터 간 데이터를 주고받을 때 에러가 발생하지 않도록 알맞게 나누어 전송하고 이를 수신하여 다시 기존에 정보로 변환하는 과정, 어떤 모델이 약속되어 있는지 알아보자

#### 계층 구조
- 네트워크 상에서 여러 대의 컴퓨터가 데이터를 주고 받으려면 이들을 서로 연동할 수 있도록 표준화된 인터페이스를 지원해야한다. OSI 7 모델과 TCP/IP 모델 모두 계층 구조를 가지고 있기 때문에 자세히 알아보기 전 먼저 계층구조가 어떤 것인지 적용하면 어떤점이 좋은지를 알 필요가 있다.
- `계층구조(Layer Structure)`는 네트워크 뿐만 아니라 운영체제 등 다양한 분야에서 적용되는데, 계층구조를 사용하는 목적은 `분할 정복(Divide and Conquer)`때문이다. 
- 어떠한 복잡한 문제를 해결하고자 할때 나누어 생각하면 쉽게 해결할 수 있다는 취지인 것이다.
- 계층 구조의 또다른 특징은 위, 아래 층으로만 이동할 수 있다는 점이고, 건너뛰어 한번에 맨위 또는 아래로 갈 수 없다. 즉, 다음 단계로 넘어가기 위해선 이전 계층이 `전제 조건`이 되어야 한다.

#### OSI 7계층 모델
- `OSI 7 Layer` 모델은 네트워크 통신 과정을 `7개의 계층`으로 구분한 산업 표준 참조 모델이다. 
- 초창기의 네트워크는 각 컴퓨터마다 시스템이 달랐기 떄문에 하드웨어와 소프트웨어의 논리적인 변경없이 통신할 수 있는 표준 모델이 나타나게 되었다. 

```js
PDU란?

- OSI 7계층에서는 PDU개념을 중요시하는데 PDU(Process Data Unit)란 각 계층에서 전송되는 단위이다. 
- 1계층에서 PDU가 비트(Bit)라고 생각하기 쉽지만 PDU라고 하지 않고 여기서 비트는 단위라기 보다는 전기 신호의 흐름일 뿐이다.
- PDU는 2계층-프레임(Frame), 3계층-패킷(Packet), 4계층-세그먼트(Segment) 만 생각하면 된다. 
- 네트워크 통신과정을 깊이 이해하기 위해서는 왜 각각의 계층의 PDU가 다른지 알아야하고, 역할에 대해 알고 있어야 한다.
```

<br />

##### 1계층 : 물리 계층(Physical Layer)
- 물리계층은 OSI 모델의 최하위 계층에 속하며, 상위 계층에서 전송된 데이터를 물리 매체(허브, 라우터, 케이블 등)를 통해 다른 시스템에 전기적 신호를 전송하는 역할을 한다.
- 즉, 기계어를 전기적 신호로 바꿔서 와이어에 실어주는 것이다. 

PDU : 비트(Bit)
프로토콜 : Modem, Cable, Fiber, RS-232C
장비 : 허브, 리피터

##### 2계층 : 데이터 링크 계층 (DataLink Layer)
- 링크 계층은 네트워크 기기들 사이의 데이터 전송을 하는 역할을 한다. 시스템 간의 오류 없는 데이터 전송을 위해 패킷을 `프레임`으로 구성하여 물리계층으로 전송한다. 3계층에서 정보를 받아 주소와 제어정보를 헤더와 테일에 추가한다. 

PDU : 프레임(Frame)
프로토콜 : 이더넷, MAC, PPP, ATM, LAN, WIFI
장비 : 브릿지, 스위치

##### 3계층 네트워크 계층(Network Layer)
- 네트워크 계층은 기기에서 데이터그램(Datagram)이 가는 경로를 설정해주는 역할을 한다.
- 라우팅 알고리즘을 사용하여 최적의 경로를 선택하고 송신측으로부터 수신측으로 전송한다.
- 이때 전송되는 데이터는 `패킷`단위로 분할하여 전송한 후 다시 합쳐진다. 2계층이 노드 대 노드 전달을 감독한다면, 3계층은 각 패킷이 목적지까지 성공적이고 효과적으로 전달되도록 한다. 

PDU : 패킷(Packet)
프로토콜 : IP, ICMP 등
장비 : 라우터, L3 스위치 

##### 4계층 전송계층 (Transport Layer)
- 발신지에서 목적지(End to End) 간 제어와 에러를 관리한다. 
- 패킷의 전송이 유효한지 확인하고 전송에 실패된 패킷을 다시 보내는 것과 같은 신뢰성있는 통신을 보장하며, 헤드에는 `세그먼트`가 포함된다. 주소 설정, 오류 및 흐름 제어, 다중화를 수행한다.

PDU : 세그먼트(Segment)
프로토콜 : TCP, UDP, ARP, RTP
장비 : 게이트 웨이, L4 스위치

##### 5계층 세션계층(Session Layer)
- 통신 세션을 구성하는 계층으로, `포트(Port)`번호를 기반으로 연결한다.
- 통신 장치 간의 상호 작용을 설정하고 유지하며 동기화한다. 
- 동시송수신(Duplex), 반이중(Half-Duplex), 전이중(Full-Duplex) 방식의 통신과 함께 체크 포인팅과 유후, 종료, 다시 시작 과정등을 수행한다.

프로토콜 : NetBIOS, SSH, TLS

##### 6계층 표현계층(Presentation Layer)
- 표현 계층은 송신측과 수신측 사이에서 `데이터의 형식`(png, jpg, jpeg ...) 을 정해준다. 받은 데이터를 코드 변환, 구문 검색, 암호화, 압축의 과정을 통해 올바른 표준 방식으로 변환해준다.

프로토콜 : JPG, MPEG, SMB, AFP

##### 7계층 응용 계층(Application Layer)
- 응용계층은 사용자와 바로 연결되어 있으며 응용 SW를 도와주는 계층이다. 
- 사용자로부터 정보를 입력받아 하위 계층으로 전달하고 하위 계층에서 전송한 데이터를 사용자에게 전달한다.
- 파일 전송, DB, 메일 전송 등 여러가지 응용 서비스를 네트워크에 연결해주는 역할을 한다.

프로토콜 : DHCP, DNS, FTP, HTTP

<br />

#### TCP/IP 모델

- 그렇지만 OSI 참조 모델은 말그대로 참조 모델일 뿐 실제 사용되는 인터넷 프로토콜은 OSI 7계층 구조를 완전히 따르지 않는다. 인터넨 프로토콜 스택(Internet Protocol Stack)은 현재 대부분 TCP/IP를 따른다.
- TCP/IP는 인터넷 프로토콜 중 가장 중요한 역할을 하는 `TCP`와 `IP`의 합성어로 데이터의 흐름관리, 정확성 확인, 패킷의 목적지 보장을 담당한다. 
- <strong>데이터의 정확성 확인은 `TCP`가, 패킷을 목적지까지 전송하는 역할을 `IP`가 수행한다.</strong>

```js
TCP/IP의 4계층

- TCP/IP는 OSI 참조 모델과 달리 표현계층, 세션계층을 응용계층에 다 포함시키고 있지만 사실상 TCP/IP 모델의 Application 계층 하나에서 Application, Presentation, Session 계층의 구현을 다 하고 있다고 이해하는게 올바르다.
```
<span align='center'>

![TCP/IP Layer](./img/TCP_IP%20Layer.PNG)
[출처] : https://velog.io/@hidaehyunlee/%EB%8D%B0%EC%9D%B4%ED%84%B0%EA%B0%80-%EC%A0%84%EB%8B%AC%EB%90%98%EB%8A%94-%EC%9B%90%EB%A6%AC-OSI-7%EA%B3%84%EC%B8%B5-%EB%AA%A8%EB%8D%B8%EA%B3%BC-TCPIP-%EB%AA%A8%EB%8D%B8

</span>

<br />

- 데이터는 아래 그림과 같이 단계별로 헤더(Data=> Segment => Datagram => Frame)를 붙여 전송하며 이를 `데이터 캡슐화`라고 한다.

<br />

<span align='center'>

![TCP/IP Layer](./img/TCP_IP%20Data.PNG)
[출처] : https://velog.io/@hidaehyunlee/%EB%8D%B0%EC%9D%B4%ED%84%B0%EA%B0%80-%EC%A0%84%EB%8B%AC%EB%90%98%EB%8A%94-%EC%9B%90%EB%A6%AC-OSI-7%EA%B3%84%EC%B8%B5-%EB%AA%A8%EB%8D%B8%EA%B3%BC-TCPIP-%EB%AA%A8%EB%8D%B8

</span>

<br />

[출처] : https://velog.io/@hidaehyunlee/%EB%8D%B0%EC%9D%B4%ED%84%B0%EA%B0%80-%EC%A0%84%EB%8B%AC%EB%90%98%EB%8A%94-%EC%9B%90%EB%A6%AC-OSI-7%EA%B3%84%EC%B8%B5-%EB%AA%A8%EB%8D%B8%EA%B3%BC-TCPIP-%EB%AA%A8%EB%8D%B8

---