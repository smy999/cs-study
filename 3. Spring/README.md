# Spring

* [Spring Framework란](#spring-framework란)
* Spring, Spring MVC, Spring Boot의 차이
* Bean이란
* Container란
* IOC(Inversion of Control, 제어의 역전)란
* MVC 패턴이란
* DI(Dependency Injection, 의존성 주입)란
* AOP(Aspect Oriented Programming)란
* POJO
* DAO와 DTO의 차이
* Spring JDBC를 이용한 데이터 접근
* Filter와 Interceptor 차이



<br>

<br>



# Spring Framework란

### Framework

편하고 안정적인 개발을 위한 도구로, 내부에서 모든 것을 해결할 수 있도록 제공하는 틀

* 필요한 여러 라이브러리 제공
* 향상된 API 제공

<br>

### Spring Framework

Java Platform을 위한 Open Source Application

* 대규모 개발을 지원하는 가벼운 프레임워크: Enterprise급 Application(기업을 대상으로하는 서비스)을 개발하기 위한 모든 기능들을 종합적으로 제공하는 경량화 Solution

* 객체의 생성 및 소멸 그리고 라이프 사이클을 관리하며 Spring Container로부터 필요한 객체를 가져와 사용한다.
* EJB에서 POJO로 바뀌면서 사용하는 구조적으로 간결해진 클래스를 제공한다.



<br>

<br>





# Spring, Spring MVC, Spring Boot의 차이











<br>

<br>



# IOC란?

Spring Framework는 IOC 기반이다. 그렇가면 IOC란 무엇인가?

**IOC는 Inversion of Control의 약자로, 제어의 역전이란 뜻을 가진다.**

일반 프로그램은 객체 생성 > 의존성 객체 생성 > 객체 내 메소드 호출 순으로 모든 관정을 사용자가 제어한다.

IOC는 일반적인 흐름 구조가 하니다. IOC에서는 객체는 사용할 객체를 선택하거나 생성하지 않으며, 자신이 어디서 만들어지고 사용되는지 모른다.

객체 자신의 모든 권한을 다른 대상에 위임하여 제어 권한을 위임받은 특정 객체에 의해 결정되고 만들어진다.

**제어의 역전이란, 객체의 생성부터 생명주기까지 기존 사용자가 모든 작업을 제어하던 것을 특정 객체에 위임하는 것을 말한다.**



| HTTP | Socket |
| ---- | ------ |
|      |        |















| 구분                    | TCP                                 | UDP                  |
| ----------------------- | ----------------------------------- | -------------------- |
| 연결 방식               | 연결형                              | 비연결형             |
| 교환 방식(단위: Packet) | Byte Stream(연결형: 가상 회선 방식) | Datagram(비연결형)   |
| 순서 여부               | 순서 보장                           | 순서 미보장          |
| 수신 확신               | 수신 여부 확인                      | 수신 여부 미확인     |
| 통신 방식               | 일대일                              | 일대일/일대다/다대다 |
| 신뢰 보장               | 신뢰 보장                           | 신뢰 미보장          |
| 속도 비교               | 느림                                | 빠름                 |
| Header 크기             |                                     |                      |

<br>

| HTTP | Socket |
| ---- | ------ |
|      |        |





<br>

<br>





## 참고자료

Spring Framework란

* https://velog.io/@seculoper235/0.-Spring-%EC%8A%A4%ED%94%84%EB%A7%81-%ED%94%84%EB%A0%88%EC%9E%84%EC%9B%8C%ED%81%AC%EB%9E%80
* https://khj93.tistory.com/entry/Spring-Spring-Framework%EB%9E%80-%EA%B8%B0%EB%B3%B8-%EA%B0%9C%EB%85%90-%ED%95%B5%EC%8B%AC-%EC%A0%95%EB%A6%AC



Spring, Spring MVC, Spring Boot의 차이

Bean이란

Container란

IOC(Inversion of Control, 제어의 역전)란

MVC 패턴이란

DI(Dependency Injection, 의존성 주입)란

AOP(Aspect Oriented Programming)란

POJO

DAO와 DTO의 차이

Spring JDBC를 이용한 데이터 접근

Filter와 Interceptor 차이

