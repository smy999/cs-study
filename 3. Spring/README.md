# Spring

* [Spring Framework란](#spring-framework란)
* [Spring, Spring MVC, Spring Boot의 차이](#Spring-Spring-MVC-Spring-Boot의-차이)
* [Bean이란](#Bean이란)
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

대규모 개발을 지원하는 가벼운 프레임워크: Enterprise급 Application(기업을 대상으로하는 서비스)을 개발하기 위한 모든 기능들을 종합적으로 제공하는 경량화 Solution

객체의 생성 및 소멸 그리고 라이프 사이클을 관리하며 Spring Container로부터 필요한 객체를 가져와 사용한다.

EJB에서 POJO로 바뀌면서 사용하는 구조적으로 간결해진 클래스를 제공한다.



<br>

<br>



# Spring, Spring MVC, Spring Boot의 차이



| Spring                                                      | Spring Boot                                                  | Spring MVC                                                   |
| ----------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Enterprise Application을 개발하는 OpenSource 경량 Framework | REST API를 개발하는데 사용되며, 기존의 Spring Framework 위에 빌드된다. | Model View이며, 웹 개발에 시용되는 Controller 기반 Web Framework |
| 의존성 주입                                                 | 자동 구성                                                    | 수동으로 빌드                                                |
| 명시적으로 Server 설정                                      | Tomcat & Jetty 등과 같은 Embedded Server를 제공              |                                                              |
| 실행 시 배치 디스크립터가 필요                              | 배치 디스크립터에 대한 요구 사항 없음                        | 배치 디스크립터 필요                                         |
| 개발자가 많은 코드를 작성                                   | 코드 길이와 개발 시간 단축, 생상성 향상                      | 개발에 더 많은 시간 소요                                     |
| 메모리 내 데이터베이스에 대한 자원을 제공하지 않음          | H2와 같은 메모리 내 데이터베이스에 대한 기원을 제공          |                                                              |
|                                                             | Layer: Presentation, Data Access, Service, Integraion        | Model, View, Controller, Front Controller                    |

<br>

<br>

# Bean이란

### Bean?

Spring IOC 컨테이너가 관리(인스턴스화, 관리, 생성)하는 자바 객체를 Bean이라고 한다.

Bean 객체는 new 연산자로 객체를 생성할 때의 객체가 아닌, ApplicationContext.getBean()으로 얻어질 수 있는 객체다.

POJO(Plain Old Java Object)를 Beans라고 한다.

POJO는 본래 자바의 장점을 살리는 특정 '기술'에 종속되어 동작하는 것이 아닌 '오래된' 방식의 '순수한' 자바 객체

Beans는 Application의 핵심을 이루는 객체로, 대부분 Container에 공급하는 설정 메타 데이터(XML 파일)에 의해 생성된다.



### 생성 1. Component Scanning

Bean을 등록할때 사용하는 Interface들을 Life Cycle Callback이라고 부른다.

Life Cycle Callback는 @Component이 붙어있는 모든 Class의 Instance를 생성해 Bean으로 등록하는 작업을 수행하는 Annotation Processor가 등록되어있다.

@ComponentScan: 어디부터 Component를 찾을 것인지 알려주는 역할 (= @Component를 찾아준다.)

@Compenent: 실제로 Bean으로 등록할 Class를 알려주는 역할

<br>



### 생성 2. Configuration

Contiguration을 사용하여 Bean을 설정하는 XML 파일에 설정하는 방법, Java Class에 설정하는 방법으로 2가지다.

* XML 파일에 설정
  * class: 정규화된 자바 Class명, 필수 기입 항목
  * id: Bean의 고유 식별자
  * scop: 객체의 범위(= singleton, prototype...)
  * constructor-arg: 생성 시 Bean constructor에 전달할 인수
  * property: 생성 시 bean setter에 전달할 인수
  * Init-method, destroy-method: 생성, 삭제 함수

```null
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xmlns:context="http://www.springframework.org/schema/context">

    <bean id="" class="com.spring.">
        <property name="" value=""></property>
    </bean>

    <bean id="" class="com.spring.">
        <property name="" value=""></property>
    </bean>
</beans>
```

* Java Class에 설정

@Bean을 사용하여 직접 등록할 수 있다.(= @Component를 붙이지 않아도 된다.)

ExampleConfiguration 객체가 IoC Container 안에 Bean으로 등록된다.

```java
@Configuration
public class ExampleConfiguration {
    @Bean
    public ExampleController exampleController() {
        return new ExampleController;
    }
}
```

<br>

### Scope

모든 Bean은 Singleton으로 생성되어 관리한다.

Spring Container에서 한 번 생성되어 사라질 때까지 Bean도 생성되어 사라진다.



# 여기부터 이어서 나중에!!

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

* http://dawoonjeong.com/spring-spring_mvc-vs-spring_boot-vs-spring_mvc/



Bean이란

* https://atoz-develop.tistory.com/entry/Spring-%EC%8A%A4%ED%94%84%EB%A7%81-%EB%B9%88Bean%EC%9D%98-%EA%B0%9C%EB%85%90%EA%B3%BC-%EC%83%9D%EC%84%B1-%EC%9B%90%EB%A6%AC
* https://velog.io/@gillog/Spring-Bean-%EC%A0%95%EB%A6%AC

Container란

IOC(Inversion of Control, 제어의 역전)란

MVC 패턴이란

DI(Dependency Injection, 의존성 주입)란

AOP(Aspect Oriented Programming)란

POJO

DAO와 DTO의 차이

Spring JDBC를 이용한 데이터 접근

Filter와 Interceptor 차이
