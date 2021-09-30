# TCP handshake

- 악수
- 연결을 성립하고 해제
  - 연결 : 3-way-handshake
  - 해제 : 4-way-handshake



## 참고

- TCP의 헤더는 10개의 필드로 구성됨
- 이중 Control Flags를 이용해 handshake에서 요청/응답 등을 표시한다.
- UAPRSF
- URG, ACK,....
  - **U**nskilled **A**ttackers **P**ester **R**eal **S**ecurity **F**olks
- sequence
  - 



## 연결 (3-way-handshake)

- TCP는 정확한 전송 보장을 위해 통신에 앞서 논리적 접속을 성립하기 위해 이 과정을 진행한다.
- ![img](https://media.geeksforgeeks.org/wp-content/uploads/TCP-connection-1.png)

- 순서
  1. 클라이언트 -> 서버 : **SYN**
  2. 서버 -> 클라이언트 : **SYN + ACK**
     1. 쌍방 연결이여야하기에 1번요청에대한 응답+내쪽에서 보내는 연결요청
  3. 클라이언트 -> 서버 : **ACK**



## 연결해제(4-way-handshake)

![img](https://media.geeksforgeeks.org/wp-content/uploads/CN.png)



- 연결때와는 달리 바로 ACK 수신후 바로 종료하는게 아니라 데이터 송수신 마저 하고 종료함
- 순서
  1. C -> S : FIN
     1. 종료한다
  2. S -> C : ACK
     1. FIN 요청 확인
     2. CLOSE_WAIT : 모든 데이터를 내보내기 위해서
  3. S -> C : FIN
     1. 데이터 모두 내보낸 후 종료
  4. C -> S : ACK
     - 종료 요청 확인
     - TIME_WAIT : 바로 종료가 아니고 서버로부터 데이터 마저 받는동기 대기
  5. 서버 종료
  6. 클라이언트 종료

