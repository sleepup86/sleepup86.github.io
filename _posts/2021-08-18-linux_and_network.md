---
layout: single
title:  "리눅스 기본명령어 및 네트워크"
categories:
  - IT
  - 경기도미래기술학교
  - 자바개발자
---

리눅스의 디렉토리 개념
	- 디렉토리는 파일묶음의 메타데이터를 저장한 파일
	- 파일시스템에 데이터가 저장되면 해당 데이터와 함께 메타데이터가 생성된다
	- 이때 이 메타데이터가 디렉토리에 등록되는것
	- cp와 touch등 파일을 복사하거나 생성하게 되면 메타데이터도 함께 생성
	- 그와 달리 mv명령의 경우 해당 메타데이터를 저장한 디렉토리만 바꿔주는것
	- 그리고 파일은 블럭단위로 쪼개져서 저장되는데, 이때 연결리스트 구조로 메타데이터는 쪼개진 데이터의 맨 앞부분 주소를 가지고 있다.
	- 포맷을 하게 되면 이 메타데이터를 지우고
	- 포렌식 기법은 메타데이터가 없지만 디스크에 남아있는 데이터를 찾아내는것

apt install tree
tree / -L 1   루트디렉토리 /에서 deepth Level을 설정(/가 0 그아래가 1)

find 경로 옵션 [인자] 실행옵션 실행명령 {} \;
	find . -name a* -exec rm {} \;	현재디렉토리의 a로시작하는 모든파일 삭제
	find /etc/systemd/ -name "*.conf" -exec more {} \;	
	
	
절대경로, 상대경로
	루트부터 시작하냐, 현재위지부터 시작하냐

touch 파일생성(존재하는 파일은 수정일시 변경)

rm 삭제
	-r 디렉토리삭제
	-i 지울지 확인
	-f 강제

퍼미션
	권한|종류	디렉토리	파일
	r 읽기	디렉토리내 파일목록	파일내 내용
	w 쓰기	디렉토리내 파일목록	파일내 내용
	x 실행	디렉토리내로 접근	파일 실행
	따라서 파일자체에 권한이 없어도 디렉토리에 w권한이 있다면 삭제가능


네트워크(OSI7 & TCP/IP)
7 앱	눈에보이는 곳, 편지지
6 프레젠테션	한글로 쓸지, 영어로 쓸지 등의 결정
5 세션	한번이라도 연결이 되어 목적지 주소를 알아야 함

4 트랜스포트	우체국 접수창구 지정 / 목적에 맞는 포트설정, TCP/UDP 결정(앱에따라결정)
3 네트워크	사람마다 다른 필기의 주소를 라벨지로 붙여서 정확한 목적지 확인
2 데이터링크	번지와 동호수 기입
1 피지컬	전기신호로 전송

윈도우 cmd창에서
netstat -n	네트워크 정보 프로토콜 출발지 목적지 상태

3way hand-shaking
	SYN - SYN/ACK - ACK

IPv4 : 32bit   8bit 단위로 옥탯이라고 말하며 4마디로 나눔
IPv6 : 128bit   16bit 단위로 8마디로 나눔

이후의 내용은 IPv4
IP는 네트워크아이디와 호스트아이디로 구분된다

공인IP : 외부와 통신가능
사설IP : 외부와 통신불가 - 내맘대로 설정가능
	10.0.0.0 ~ 10.255.255.255 / 8
	172.16.0.0 ~ 172.31.255.255 / 12
	192.168.0.0 ~ 192.168.255.255 / 16
	서브넷팅을 통해 알아서 네트워크 사이즈를 구성하여 사용


ARP - 라우터가 ip주소와 mac주소를 매칭시켜 학습하는 프로토콜
	arp -a	arp테이블 확인

브로드캐스트	전체방송
유니캐스트	1:1 통신
멀티캐스트	1:N 통신
애니캐스트	하나의 IP공유하는 서버 중 가장 지연시간이 낮은 서버가 응답

ICMP 패킷 전송에 실패했을 때 에러 알림(DDoS공격에 많이 이용되는 프로토콜)
	ping 통신상태 확인
	traceroute(윈도우cmd : tracert) 통신 구간별 확인(어느 구간의 문제인지 확인가능)
	DDoS공격에 많이 이용되는 프로토콜
  따라서 기본적으로 방화벽이 ICMP를 막아놨음
