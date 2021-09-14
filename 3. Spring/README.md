# Spring

* [Spring Framework란](#spring-framework란)
* [Spring, Spring MVC, Spring Boot의 차이](#Spring-Spring-MVC-Spring-Boot의-차이)
* [Bean이란](#Bean이란)
* [Container란](#Container란)
* [IoC(Inversion of Control, 제어의 역전)란](#IOC란)
* [MVC 패턴이란](#MVC-패턴이란)
* [DI(Dependency Injection, 의존성 주입)란](#DIDependency-Injection-의존성 주입란)
* [AOP(Aspect Oriented Programming)란](#AOPAspect-Oriented-Programming란)
* [POJO란](#POJO란)
* [DAO와 DTO의 차이](#DTO와-DAO의-차이)
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

### Spring Framework 구조 - 그림 추가하기

<br>

### Spring Framework 모듈 - 그림 추가하기

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

Spring IoC 컨테이너가 관리(인스턴스화, 관리, 생성)하는 자바 객체를 Bean이라고 한다.

Bean 객체는 new 연산자로 객체를 생성할 때의 객체가 아닌, ApplicationContext.getBean()으로 얻어질 수 있는 객체다.

POJO(Plain Old Java Object)를 Beans라고 한다.

POJO는 본래 자바의 장점을 살리는 특정 '기술'에 종속되어 동작하는 것이 아닌 '오래된' 방식의 '순수한' 자바 객체

Beans는 Application의 핵심을 이루는 객체로, 대부분 Container에 공급하는 설정 메타 데이터(XML 파일)에 의해 생성된다.

<br>

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

모든 Bean은 Singleton으로 생성되어 관리한다. (명시되지 않으면 Singleton으로 생성)

Spring Container에서 한 번 생성되어 사라질 때까지 Bean도 생성되어 사라진다.

![스크린샷 2021-09-06 오후 7 22 44](https://user-images.githubusercontent.com/33407191/132202747-9e75dc9b-c657-4144-991e-68d840562c94.png)

<br>
<br>

# Container

### 개념

주입을 이용하여 객체를 관리하는 것이 Container다.

Container는 객체관리를 주로 수행하는 그릇

Bean의 생성과 관계, 사용, 생명 주기 등을 관장

의존성 제어, 즉 객체 간의 의존성을 낮추기 위해 Spring 컨테이너가 사용
(= Container 가 Bean 을 관리해주기 때문에, 개발자는 모듈 간에 의존 및 결합으로 인해 발생하는 문제로부터 자유로워 졌다.

Annotaion 만 남겨주면 Container 가 개발자가 원하는 상황에 코드를 실행
(= 메서드가 언제, 어디서 호출되어야 하는지 그리고 메서드를 호출하기 위해 필요한 매개 변수를 준비해서 Container 가 개발자 대신 알아서 호출)

<br>
<br>


# IoC란

Spring Framework는 IoC 기반이다. 그렇가면 IoC란 무엇인가?

**IOC는 Inversion of Control의 약자로, 제어의 역전이란 뜻을 가진다.**

일반 프로그램은 객체 생성 > 의존성 객체 생성 > 객체 내 메소드 호출 순으로 모든 관정을 사용자가 제어한다.

IOC는 일반적인 흐름 구조가 하니다. IOC에서는 객체는 사용할 객체를 선택하거나 생성하지 않으며, 자신이 어디서 만들어지고 사용되는지 모른다.

객체 자신의 모든 권한을 다른 대상에 위임하여 제어 권한을 위임받은 특정 객체에 의해 결정되고 만들어진다.

**제어의 역전이란, 객체의 생성부터 생명주기까지 기존 사용자가 모든 작업을 제어하던 것을 특정 객체에 위임하는 것을 말한다.**



<br>

<br>



# MVC 패턴이란

MVC 는 Model, View, Controller의 약자로, 하나의 애플리케이션, 프로젝트를 구성할 때 그 구성요소를 세가지의 역할로 구분한 패턴이다. (= 소프트웨어 디자인 패턴)

사용자가 controller를 조작하면 controller는 model을 통해서 데이터를 가져오고 그 정보를 바탕으로 시각적인 표현을 담당하는 View를 제어해서 사용자에게 전달한다.




| 구분       | 설명                                                         |
| ---------- | ------------------------------------------------------------ |
| Model      | - 어떤 동작을 수행하는 코드<br>- 순수 Public 함수로만 이루지며, 몇몇 함수들은 사용자 질의(query)에 대한 정보를 담는다. |
| View       | - Model은 여러 개의 View를 가질 수 있다.<br>- View는 Model에게 질의하여 Model로부터 값을 가져와 사용자에게 보여준다. (= 데이터 및 객체의 입출력을 담당)<br>- 사용자 인터페이스 요소로 사용자가 직접 볼 수 있는 화면을 의미한다. |
| Controller | - View는 여러 개의 Controller를 가진다.<br>- 프로그램의 작동 순서, 방식을 제어한다.<br>- 사용자는 Controller를 통해 Model의 상태를 변경하거나 다른 클래스에게 알릴 수 있는 함수가 필요하다. |



<br>

<br>



# DI(Dependency Injection, 의존성 주입)란

### Object Dependencies(객체 의존성)

* 현재 객체가 다른 객체와 상호작용(참조)하고 있다면 현재 객체는 다른 객체에 의존성을 가진다.
* 즉, 하나의 모듈이 바뀌면 의존한 다른 모듈까지 변경 되어야 한다.
* 또한 두 객체 사이의 의존성이 존재하면 Unit Test 작성이 어려워 진다.



<br>



### Dependency Injection(의존성 주입)

* 객체 자체가 아니라 Framework에 의해 객체의 의존성이 주입되는 설계 패턴
* Framework에 의해 동적으로 주입되므로 여러 객체 간의 결합이 줄어든다.
* Dependency Injection은 Spring Framework에서 지원하는 IoC의 형태



<br>



### IoC(제어의 역전): 프로그램 제어권을 framework가 가져가는 것

* 개발자가 모든 제어의 중심이지만 코드 전체에 대한 제어는 framework가 한다.
* 개발자가 설정(xml, annotation 등)만 하면 Container가 알아서 처리한다.
* 즉, 우리는 Framework 속에서 프로그래밍을 하는 것.



<br>



Container가 Bean 객체를 생성한 후, 종속성을 주입한다.

##### Dependency Injection(의존성 주입)과 Inversion Of Control(제어의 역전)은 같은 의미로 사용된다. = IoC는 DI를 통해 달성된다.



<br>



### 의존성 주입하기(3가지 방법)

1. Contructor Injection: 생성자를 통한 전달
   <constructor-arg ref="cat"></constructor-arg>

2. Method(Setter) Injection: setter() method를 이용한 전달
   <property name="myName" value="poodle"></property>

3. Field Injection: 멤버 변수를 통한 전달

   

<br>

<br>



# AOP(Aspect Oriented Programming)란

##### Aspect Oriented Programming

##### 여러곳에 흩여저 있는 공통 기능을 한곳에 모아서 관리하자.



<br>



### Spring Boot에서 구현하는 방법

1. Spring Boot AOP Dependency

```xml
<dependency> 
	<groupId>org.springframework.boot</groupId> 
	<artifactId>spring-boot-starter-aop</artifactId> 
</dependency>
```

2. AOP 관련 class를 Bean으로 생성 후 공통 기능 작성

- @Component: @Aspect는 @Component를 갖지 않기 때문에 설정해줘야 한다.
- @Aspect: AOP라는 것을 알려주는 Annotation이다.
- @Around: 공통기능을 기능 전후에 모두 실행할 때 사용한다.
  - execution: 실행
  - 리턴타입: execution(*)에서 *, 이 경우는 모든 타입
  - com.example.demo.controller.*Controller.*(..)): com.example.demo.controller.*Controller 하위의 모든 class method에 대해서 적용된다.
  - joinPoint.proceed(): 공통기능 실행

```xml
@Component 
@Aspect 
public class LoggerAspect { 
	// 공통 기능 구현부
	@Around("execution(* com.example.demo.controller.*Controller.*(..))") 
	public Object logPrint(ProceedingJoinPoint joinPoint) throws Throwable { 
		log.info("Before Execute Method!!!"); 
		Object proceed = joinPoint.proceed(); 
		log.info("After Execute Method!!!!"); 
		return proceed; 
	}
}
```



<br>

<br>



# POJO란

### POJO = Java Beans

* 여기서 Java Beans는 Sun의 Java Beans나 EJB의 Bean을 뜻하는것이 아닌 순수하게 setter, getter 메소드로 이루어진 Value Object성의 Bean을 말한다.
* 특별한 제한에 종속되지 않고, 클래스 패스(class path)를 필요로 하지 않는 일반적인 Java Object를 의미합니다.
* "POJO"라는 용어는 주요 Java 오브젝트 모델, 컨벤션 또는 프레임워크를 따르지 않는 '순수한' Java 오브젝트를 나타낸다.



<br>



### POJO가 Bean이라면 왜 굳이 다르게 부르는가?

Beans라는 용어로 위의 깡통 빈 클래스를 정의하기에는 Java Beans나 EJB의 Beans와 구분이 모호하고 또한 Beans라는 용어로 정의되는 여타 다른 개념들과의 확실한 분리를 위해 POJO라는 용어를 사용한다.

Java Beans는 특별한 POJO의 변형이라고 볼 수 있다. 더 세부적인 규약이 정해져있고, 이를 지켜야한다.



<br>



### 장점

자바의 객체지향적인 특징을 살려 비즈니스 로직에 충실한 개발이 가능하다.

<br>

<br>





# DTO와 DAO의 차이

* DTO(Data Tranfer Object): 특정 테이블의 정보를 레코드 단위로 정의한 Class
* DAO(Data Access Object): 데이터베이스에 접속하고 명령을 전송하는 Class



### DTO(Data Tranfer Object)

계층간 데이터를 교환하는 Java Beans이다.

데이터베이스 레코드의 데이터를 매핑하기 위한 데이터 객체를 의미한다.

DTO는 보통 로직을 갖지 않으며, data와 그 data의 접근을 위한 Getter와 Setter만을 가진다.

결국, 데이터베이스에서 data를 얻어 Service 혹은 Controller에 보내는 역할을 하는 것이 DTO이다.

VO라고도 표현하기도 한다. 하지만 둘은 차이점이 있다. VO는 값 객체로서 값을 위해 쓰인다. 자바는 값의 형을 표현하기 위해 불편 클래스를 만들어서 사용하는데, 불변은 Read-Only라는 특징을 갖는다. 반면, 넣어진 데이터를 Getter를 통해 사용한다는 공통점이 있다.



### DAO(Data Access Object)

데이터베이스의 data에 접근하기 위한 객체이다.

데이터베이스 접근을 위한 로직과 비즈니스 로직을 분리하기 위해 사용한다.

사용자는 자신이 필요한 Interface를 DAO에게 던지고 DAO는 이 Interface를 구현한 객체를 사용자에게 편라히게 사용할 수 있도록 반환한다.

DAO는 데이터베이스와 연결하는 Connectin까지 설정되어 있는 경우가 대부분이다.

예를들어 MyBatis 등을 사용하는 경우 커넥션풀까지 제공하기 때문에 DAO를 별도로 만드는 경우는 드물다.









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

* https://ibocon.tistory.com/122

IOC(Inversion of Control, 제어의 역전)란

MVC 패턴이란

* https://m.blog.naver.com/jhc9639/220967034588
* https://velog.io/@arielgv829/Spring-SpringMVC-SpringBoot

DI(Dependency Injection, 의존성 주입)란

* https://gmlwjd9405.github.io/2018/11/09/dependency-injection.html

AOP(Aspect Oriented Programming)란

POJO

* https://velog.io/@dion/what-is-POJO

DAO와 DTO의 차이

* https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=godwings&logNo=221048712980
* https://m.blog.naver.com/cjhol2107/221757079506

Spring JDBC를 이용한 데이터 접근

Filter와 Interceptor 차이
