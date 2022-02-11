# Data Structure

- [Java란?](#Java란)
- [Java Platform](#Java-Platform)


<br>



# Java란?

### Java?

﻿썬 마이크로시스템즈의 제임스 고슬링(James Gosling)과 다른 연구원들이 개발한 객체지향적 프로그래밍 언어

<br>

초기 가전제품 내에 탑재해 동작하는 프로그램을 위해 개발했지만 현재 웹 애플리케이션 개발에 가장 많이 사용하는 언어 가운데 하나이고, 모바일 기기용 소프트웨어 개발에도 널리 사용하고 있다.

<br>

자바를 다른 컴파일 언어와 구분 짓는 가장 큰 특징은 컴파일된 코드가 플랫폼 독립적이라는 점이다.



<br>



### **객체지향?**

Object-Oriented Programming, OOP

<br>

컴퓨터 프로그램을 명령어의 목록으로 보는 시각에서 벗어나 여러 개의 독립된 단위, 즉 "객체"들의 모임으로 파악하고자 하는 것이다. 각각의 객체는 메시지를 주고받고, 데이터를 처리할 수 있다.

객체지향은 '객체(object)'라는 기본 단위로 나누고 이들의 상호작용으로 서술하는 방식이다. 객체란 하나의 역할을 수행하는 '메서드와 변수(데이터)'의 묶음으로 본다.

<br>

객체 지향 프로그래밍은 프로그램을 유연하고 변경이 쉽게 만들기 때문에 대규모 소프트웨어 개발에 많이 사용된다.

또한 프로그래밍을 더 배우기 쉽게 하고 소프트웨어 개발과 보수를 간편하게 하며, 보다 직관적인 코드 분석을 가능하게 하는 장점이 있다.



<br>



### **플랫폼 독립적?**

자바로 개발된 프로그램은 CPU나 운영 체제의 종류에 관계없이 JVM을 설치할 수 있는 시스템에서는 어디서나 실행할 수 있다.

<br>

→ 자바 컴파일러는 자바 언어로 작성된 프로그램을 바이트코드라는 특수한 클래스 파일(.class)로 변환한다.

→ JVM을 활용하여 클래스  파일을 읽어 기계어로 변환한다.

<br>

바이트코드를 실행하기 위해서는 JVM(자바 가상 머신, Java Virtual Machine)이라는 특수한 가상 머신이 필요한데, 이 가상 머신은 자바 바이트코드를 어느 플랫폼에서나 동일한 형태로 실행시킨다.

=  Java로 작성된 프로그램은 플랫폼에 맞는 JVM만 설치되어 있으면 문제없이 동작한다.

= 이러한 구조가 웹 애플리케이션의 특성과 맞아떨어져 인기를 끌게 되었다.





<br>



### **쉽다!**

C와 C++의 문법을 차용했지만 포인터와 다중 상속과 같은 어려운 개념을 제외했다. 따라서 문법적으로 이해하기 쉽다.



<br>

<br>



# Java Platform

플랫폼? 프로그램이 실행될 수 있는 하드웨어 및 소프트웨어 환경을 의미\



<br>



### **자바 프로그래밍 플랫폼?**

자바 플랫폼은 자바 언어로 작성된 프로그램이 실행되는 특정 환경을 의미

모든 자바 플랫폼은 JVM과 API로 구성된다.

<br>

**자바의 4개 플랫폼**

\- Java SE(Standard Edition)

\- Java EE(Enterprise Edition)

\- Java ME(Micro Edition)

\- Java FX



<br>



### **Java SE**

가장 기본이 되는 에디션, 자바 언어 대부분의 패키지가 포함

우리가 일반적으로 설치하는 JDK가 Java SE JDK이며, 자바 언어라고 하는 대부분은 패키지를 포함한다.

java.lang.*, java.io.*, java.util.*, java.awt.*, javax.rmi.*, javax.net.*

<br>

자바 언어의 핵심 기능 제공

Basic Type, Networking, Security, Database access, GUI, XML Parsing 등

<br>

자바 애플리케이션 구현 시 흔히 사용되는 라이브러리 제공

Virtual Machine, Development tool, deployment tools, deployment technology

<br>

테스크톱, 서버, 임베디드 시스템을 위한 표준 자바 플랫폼으로 가장 일반적으로 사용



<br>



### **Java EE**

자바로 웹 개발을 할 수 있게 하는 표준

'기업용 에디션' → 대규모(large-scale), 다계층(multi-tiered), 확장 가능(scalable), 안정적 네트워크(secure network) 애플리케이션을 개발 및 실행하기 위한 API/런타임 환경 제공

<br>

Java SE를 기반으로 서버 개발을 위한 다양한 기술 제공

웹 프로그래밍에서 가장 많이 사용되는 JSP, Servlet, DB와 연동하는 JDBC, JNDI, JTA, EJB, RMI, XML, JMS, Java IDL, JTS, Java Mail, JAF 등을 제공

현업에서 사용되는 API의 집약



<br>



### **Java ME**

'임베디드'를 위한 자바 플랫폼

제한된 자원을 갖는 휴대전화, 셋톱박스에서 자바 언어를 사용하기 위해 만들어진 플랫폼

최근 스마트폰이 대중화되고 업체별로 자체 OS를 사용하기 때문에 잘 사용되지 않는다.



<br>



### **Java FX**

데스크톱 애플리케이션과 리치 인터넷 애플리케이션(RIA)를 개발/배포하는 소프트웨어 플랫폼

다양한 장치에서 실행 가능

Java SE를 위한 표준 GUI 라이브러리로 스윙을 대체하기 위한 고안됨

Microsoft의 Window, Linux, MacOS의 데스크톱과 웹브라우저 지원



<br>



### **Java SE vs Java EE (차이점)**

일반 웹 개발자의 경우 SE, 일반형이 아닌 기업용이나 서버(tomcat) 등 자체 생산하는 경우 EE

Java SE나 Java EE나 모두 bin 디렉터리 안의 같은 java.exe, javac.exe를 사용

Java EE는 Java SE에서 API(lib 디렉터리에 포함되어 있는 JAR 파일들)가 추가된 것이다.



<br>



### **자바 패키지**

자바 언어는 작고 단순한 구조이지만 API로 많은 기능을 제공한다.

| java.applet | 애플릿 작성에 필요한 기능을 모아 놓은 패키지                 |
| ----------- | ------------------------------------------------------------ |
| java.awt    | GUI 작성과 관련된 패키지javax.swing 패키지와 함께 자바 GUI 애플리케이션 작성 시 필수적으로 사용한다.버튼, 텍스트 필드, 메뉴 등 관련 컴포넌트와 이벤트 기능을 제공한다. |
| xjava.io    | 자바의 입출력 기능과 관련된 패키지파일이나 버퍼들의 입출력 기능을 제공한다. |
| java.lang   | 자바 언어의 기초적인 사항을 정의한 클래스와 관련된 패키지Object 클래스, 문자열 관련, 시스템 관련, 멀티 스레드 관련 기본적인 기능을 포함한다. |
| java.net    | 자바의 네트워크와 관련된 패키지이 패키지 내에는 소켓과 관련된 기능을 제공한다. |
| javax.swing | java.awt 패키지와 더불어 자바 GUI 애플리케이션 기능과 관련된 패키지java.awt 포함 내용보다 다양하고, 융통성 있는 컴포넌트를 제공한다. |
| java.util   | 유틸리티성 기능과 관련된 패키지날짜 표현이나 여러 자료형을 하나로 취급하는 컬렉션과 관련된 기능을 제공한다. |



<br>

<br>













<br>

<br>



## 참고자료

Java 란?

- [https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4)](https://ko.wikipedia.org/wiki/자바_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4))
- [https://edu.goorm.io/learn/lecture/12243/%ED%95%9C-%EB%88%88%EC%97%90-%EB%81%9D%EB%82%B4%EB%8A%94-%EC%9E%90%EB%B0%94-%EA%B8%B0%EC%B4%88/lesson/534737/%EC%9E%90%EB%B0%94%EB%9E%80](https://edu.goorm.io/learn/lecture/12243/한-눈에-끝내는-자바-기초/lesson/534737/자바란)
- https://minsoolog.tistory.com/16
- https://devchopin.com/blog/65/
- [https://ko.wikipedia.org/wiki/%EA%B0%9D%EC%B2%B4_%EC%A7%80%ED%96%A5_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D](https://ko.wikipedia.org/wiki/객체_지향_프로그래밍)

Java Plarform

- https://techvu.dev/135
- [https://hashcode.co.kr/questions/669/%EC%9E%90%EB%B0%94%EC%97%90%EC%84%9C-seeeme%EC%9D%98-%EC%B0%A8%EC%9D%B4%EA%B0%80-%EB%AD%94%EA%B0%80%EC%9A%94](https://hashcode.co.kr/questions/669/자바에서-seeeme의-차이가-뭔가요)
- https://velog.io/@jihoson94/Java-SE-vs-EE
- https://youngram2.tistory.com/80
- https://kys4871.tistory.com/74
- https://doozi316.github.io/java/2020/07/01/WEB20/





<br>
