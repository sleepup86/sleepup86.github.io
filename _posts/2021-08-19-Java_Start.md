---
layout: single
title:  "자바 시작!!"
categories:
  - IT
  - 경기도미래기술학교
  - 자바개발자
---

	- 목차
	자바의 특징
	jdk의 구조
	개발환경 설치 및 설정
	자바 프로그램 생성과정
	자바 가상 머신의 구조와 동작
	통합개발환경 이클립스 설치 및 특징
	변수


자바언어의 특징
객체지향언어(Object-Oriented Programming)
플랫폼에 독립적
	사용하던 프로그램을 다른 플랫폼에서 컴파일 할 필요없이
	바이트코드만으로 사용가능하다는 의미

자바를 사용하요 개발하기 위해서는
JDK(Java Development Kit)을 받아야함
수업은 Java SE 11(스탠다드 에디션) - 교육용은 무료 라이센스
최신버전인 16은 다른 프로그램과 아직 호환 안되는 문제가 있음
JDK = JRE(Java Runtime Environment) + 개발도구
	  JRE = JVM(Java Virtual Machine) + 라이브러리 클래스

자바의 소스파일은 java라는 확장자를 가지며
컴파일과정을 통해 바이트코드(class 확장자)이 생기며
이 바이트코드를 JVM에서 해석되며 프로그램 실행이 된다

설치 후에는 cmd창에서 아무곳에서나 자바명령어를 사용할 수 있도록
JAVA_HOME과 Path 환경변수를 설정해준다
JAVA_HOME은 설치경로
Path에는 JAVA_HOME의 bin파일을 넣어주면 된다
한번에 다 Path에 넣지 않고 자바홈을 이용하는 이유는
해당 환경변수 자체를 이용하는 프로그램도 있고
나중에 자바버전관리시 자바홈에서만 경로를 바꿔주면
패스에 반영하기 쉽기 때문이다.

메모장에서도 Hello.java 프로그램을 만들어서
파일형식을 "텍스트" 에서 "모두" 로 바꾸고
코딩에 한글이 있다면, 인코딩 유형을 "UTF-8" 에서 "ANSI" 로 바꿔 저장
	윈도우 명령프롬프트에서는 아스키 기반 코드페이지(안시)를 사용하고
	한글 윈도우는 CP949 코드페이지를 사용하므로 UTF-8로 된 코드를 CP949
	로 읽어들여 컴파일 하므로 오류가 발생
	javac -encoding utf-8 Hello.java
	위의 명령으로 인코딩 타입을 지정하여 문제 해결이 가능하고
	굳이 인코딩명령을 줄 필요없이 안시유형으로 코드를 짜면 제대로 된 안시코드를
	읽어 들여 컴파일하므로 문제 해결

해당 파일이 있는 폴더로 이동하여
javac Hello.java 를 이용하여 해당 파일을 컴파일한다
그러면 바이트코드인 Hello.class 파일이 생성된다
java Hello를 이용하여 해당 바이트코드를 JVM에 올려 실행한다
	이때 java파일을 치면 안되는데
	이유는 java파일을 읽는게 아닌 class파일을 읽어서 실행하기 때문

전체 과정을 보자면, 하드웨어 위에 OS 위에 JVM이 위치한 상태에서
소스코드 - 컴파일 - 바이트코드 - 클래스로더 - 런타임데이터영역 - 익시큐션엔진
	참고로
	Runtime Data Area에는
	Method_Area, Heap_Area, Stack_Area, PC_Register, Native_Method_Stack
	메소드영역, 힙영역, 스택영역, pc레지스터, 네이티브메소드스택이 있음
	
JVM에서
클래스 로더가 JVM으로 .class파일을 로드하여
클래스 및 관련 내용을 런타임데이터영역에 배치하고
Execution Engine에서 main부터 시작하여 바이트코드를 해석하며 프로그램 실행

메모장에서 작업하는건 에러잡기도 힘들고 사용하기 힘드므로
개발을 위한 통합개발환경(IDE, Integrated Development Environment)으로
Eclipse를 사용
	교육과정에서는 뒤에 스프링부트등의 연동을 위해 2020-03 버전을 사용
	이때 마찬가지로 자바 11부터 패키지를 보다 큰단위인 모듈을 제공하는데
	뒷과정과의 연동을 위해 모듈은 사용하지 않는다

이때 자바 개발만한다면
자바개발자(Eclipse IDE for Java Developers) 버전을 받으면 되지만,
웹개발도 하기 위해서 엔터프라이즈 자바 개발자 버전을 받을것
(Eclipse IDE for Enterprise Java Developers)

이클립스를 설치했다면 workspace를 만들어 모든 프로젝트를 관리하는 폴더를 생성
해당 workspace를 사용하여 런치한다.
	workspace를 바꾸고 싶다면 메뉴의 File - Swich Workspace에서 설정가능
이클립스 내에는 프로젝트단위로 패키지가 관리되므로 프로젝트를 생성하고
그 안에서 클래스를 생성하여 작업
처음 실행하면 퍼스펙티브라고 하여 개발에 적합한 뷰들로 구성되어 있는데
해당 모드가 Java EE로 되어 있는데 이걸 Java로 변경하는게 좋다
퍼스펙티브는 메뉴의 Window - Perspective란에서 설정하거나
우측상단의 아이콘을 통해 조절가능
그외 다크모드, 폰트, 클래스등 텍스트 내용별 색을 지정하기 위한 신택스컬러 등을
Window - Perferences 에서 설정한다.

이클립스는 저장하면 자동 컴파일러 되므로 저장하고 실행하면 된다.

변수란 데이터를 저장할 수 있는 메모리 공간으로 저장된 값은 변할 수 있다.
변수의 선언은 해당 자료형 크기의 메모리를 할당하는 작업
리터럴은 변하지 않는 데이터 자체를 의미하며, 사용자(개발자)가 지정한 고정된 값을 의미하며 int a = 10; 이라고할때 10이라는 값 자체를 의미한다.
	근데 솔직히 대체 왜 이 리터럴이라는 개념을 알아야 하는지는 모르겠음

자료형에는 기본자료형과 참조자료형으로 구분되며
기본자료형 8가지를 제외한 나머지 모두가 참조자료형이다
기본자료형에는
boolean, char, byte, short, int, long, float, double이 있다.
하드용량이 많은 지금 크게 바이트를 따지며 사용할 일은 없을꺼같고
정수형에서는 int를 가장 많이 쓰고
실수형에서는 double을 많이 사용
long은 L/l, float는 F/f가 뒤에 붙어서 나온다는 점만 기억

정수에는 10진수 외에 2, 8, 16진수가 있음
2진수는 0b101
8진수는 0123
16진수는 0x1f2
형식으로 0b, 0, 0x가 붙어 사용
실수형에서는 10진수 외에는 표현이 안되는듯

기본형은 변수에 값 자체를 저장하지만,
참조자료형은 변수에 값의 주소를 저장한다.
이때 이 주소를 이용해 배열과 같은 여러값을 이용가능하게 된다.
참조자료형 변수는 스택영역에 올라오게되고,
실제 값은 힙영역에 생성되어 있다.


이클립스
Ctrl + Space	자동완성
Ctrl + Shift + f	들여쓰기 정리
Ctrl + F11	run as 의 자바 어플리케이션으로 실행

주석
Ctrl + /	한줄 주석	다시 누르면 주석취소
Ctrl + Shift + /	여러줄 주석	Ctrl + Shift + \ 취소

Window - Preferences
general - appearance	다크 모드 등 테마 변경가능
font(general-appear-color and font)	basic - text font를 선택하여 폰트변경
java - editor - sysntax color	원하는 클래스 등의 색깔 지정
![image](https://user-images.githubusercontent.com/73269113/130158775-7bb4c11c-623d-4c19-89e1-1b1bf5a0402f.png)
