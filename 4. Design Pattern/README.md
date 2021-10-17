# Design Pattern

* [Design Pattern의 개념과 종류](#Design-Pattern의-개념과-종류)
* [Singleton Pattern](#Singleton-Pattern)
* [Strategy Pattern](#Strategy-Pattern)
* [Template Method Pattern](#Template-Method-Pattern)
* [Factory Method Pattern](#Factory-Method-Pattern)
* [MVC vs MVC2 Pattern](#MVC1-vs-MVC2-Pattern)



<br>

<br>



# Design Pattern의 개념과 종류

### Design Pattern이란?

소프트웨어 공학에서 특정 문맥에서 공통적으로 발생하는 문제에 대해 재사용 가능한 해결책이다. 소스나 기계 코드로 바로 전환될수 있는 완성된 디자인은 아니며, 다른 상황에 맞게 사용될 수 있는 문제들을 해결하는데에 쓰이는 서술이나 템플릿이다. 디자인 패턴은 프로그래머가 어플리케이션이나 시스템을 디자인할 때 공통된 문제들을 해결하는데에 쓰이는 형식화 된 가장 좋은 관행이다.

* "효율적인 코드를 위한 방법론": 소프트웨어를 설계할 때 틀정 맥학에서 자주 발생하는 고질적인 문제들이 또 발생했을 때 재사용할 수 있는 해결책
* Pattern: 다른 소프트웨어 모듈이나 기능을 가진 다양한 응용소프트웨어 시스템들을 객발할 때 서로 공통되는 설계 문제가 존재하여 이를 처리하는 공통된 해결책(설계 및 문제해결의 유사한 방법)
* Pattern은 공통의 언어를 만들어주며 개발자 사이의 소통을 원할하게 해주는 역할을 한다.

<br>

### Design Pattern 구조

* Context: 문제 발생 상황.  Pattern이 적용되는 상황
* Problem: Pattern이 적용되어 해결할 여러가지 디자인 이슈
* Solution: 문제를 해결하도록 설계를 구성하는 요소들과 요소 사이의 관계, 책임, 협력 관계를 기술한 것으로, Solution은 구체적인 구현 방법이나 언어에 의존적이지 않으면 다양한 상황에 적용할 수 있는 일족의 템플릿이다.

<br>

### Design Pattern의 종류

Design Pattern은 23가지의 디자인 패턴을 정리하소 각각의 Pattern을 생성(Creational), 구조(Structural), 행위(Behavioral) 3가지로 분류한다.


|        | Creational Pattern                                           | Structural Pattern                                           | Behavioral Pattern                                           |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Class  | Factory                                                      | Adaptor(Class)                                               | Interpreter<br>Template Method                               |
| Object | Prototype<br>Builder<br>Abstract Factory<br>Factory Method<br>Singleton<br> | Adaptor(Object)<br>Bridge<br>Composite<br>Decorator<br>Facade<br>Flyweight<br>Proxy | Command<br>Mediator<br>Memento<br>Iterator<br>Observer<br>State<br>Strategy<br>Visitor<br>Chain of Responsibility |

<br>

#### Creational Pattern

객체 생성에 관련된 Pattern

객체의 생성과 조합을 캡슐화해 특정 객체가 생성되거나 변경되어도 프로그램 구조에 영향을 받지 않도록 유연성을 제공한다.

1. Prototype: 생성할 객체의 종류를 명시하는데 원형이 되는 예시물을 이용하고 이 원형들을 복사함으로써 새로운 객체를 생성한다.
2. Builder: 복합 객체의 생성과정과 표현 정을 분리시켜 동일한 생성과정에서 다양한 표현을 생성한다.
3. Abstract Facotry: 구체적인 클래스를 지정하지 않고 관련성이 있거나 독립적인 객체들을 생성하기 위한 인터페이스를 제공한다. 
4. Factory Method: 객체를 생성하는 인터페이스를 정의하지만 인스턴스를 만드는 클래스는 서브 클래스에서 결정하도록 한다. Factory Method에서는 인스턴스를 만드는 것을 서브 클래스에서 수행한다.
5. Singleton: 클래스의 객체가 하나임을 보장하고 접근할 수 있는 전역적인 접근점을 제공한다.

<br>

#### Structural Pattern

클래스와 객체를 조합해 더 큰 구조를 만드는 Pattern

서로 다른 인터페이스를 지닌 2개의 객체를 묶어 단인 인터페이스를 제공하거나 객체들을 서로 묶어 새로운 기능을 제공한다.

1. Adaptor: 클래스의 인터페이스를 사용자가 기대하는 다른 인터페이스로 변환하는 페턴으로, 호환성이 없는 인터페이스 때문에 함께 동작할 수 없는 클래스들이 함께 작동하도록 해준다.
2. Bridge: 구현부에 추상층을 분리해 각자 독립적으로 변형할 수 있도록 한다.
3. Composite: 객체들의 관계를 트리 구조로 고성하여 부분-전체 계층을 표현한다. 사용자가 단일/복합 객체 모두 동일하게 다룰 수 있도록 한다.
4. Decorator: 주어진 상황 및 용도에 따라 어떤 객체에 책임을 덧붙이는 패턴으로, 기능 확장이 필요할 때 서브 클래스 대신 쓸 수 있는 대안이 된다.
5. Facade: 서브 시스템에 있는 인터페이스 집합에 통합된 하나의 인터페이스를 제공한다. 서브 시스템을 좀 더 쉽게 사용하기 위해 고수준의 인터페이스를 정의한다.
6. Proxy: 어떤 다른 객체로 접근하는 것을 통제하기 위해 그 객체의 매니저 또는 자리 채움자를 제공한다.

<br>

#### Behavioral Pattern

클래스와 객체 사이의 알고리즘이나 책임 분배에 관련된 Pattern

한 객체가 혼자 수행할 수 없는 작업을 여러 개의 객체로 어떻게 분배하는지, 또 그 객체 사이의 결합도를 어떨게 최소와 할 것인가에 중점을 둔다.

1. Interpreter: 주어진 언어에 대해서 문법을 위한 표현 수단을 정의하고 해단 언어로 된 문장을 해석하는 해석기를 사용한다.
2. Template: 객체의 연산에서 알고리즘의 뼈대만 정의하고 나머지는 서브 클래스에서 이루어지게 하는 것으로, Template Pattern은 알고리즘의 구조는 변경하지 않고 알고리즘의 각 단계를 서브 클래스에서 재정의한다.
3. Command: 요청을 객체로 캡슐화하여 서로 다른 사용자의 매개변수화, 요정 저장 또는 로깅, 연산의 취소를 지원한다.
4. Mediator: 한 집한에 속해있는 객체들의 상호작용을 캡슐화하는 객체를 정의한다. 중재자는 객체들이 직접 서로 참조하지 않도록하여 객체들간의 느슨한 연결을 촉진시키며 객체들의 상호작용을 독립적으로 다양화 시킬 수 있다.
5. Iterator: 내부 표현부를 노출하기 않고 어떤 객체의 집합 원소들을 순차적으로 접근하는 방법을 제공한다.
6. Observer: 객체들 사이에 1:N 의존관계를 정의하여 어떤 객체의상태가 변할 때, 의존관계 있는 모든 객체들이 통지받고 자동 갱신되게 한다.
7. State: 객체의 내부 상태가 변경될 때 행동을 변경하도록 허락한다. 객체는 자신의. 클래스가 변경되는 것처럼 보인다.
8. Strategy: 동일 계열의 알고리즘을 정의하고, 각각 캡슐화하여 객체간의 상호교환을 가능하게 한다. 알고리즘을 사용하는 사용자로부터 독립적으로 알고리즘이 변경될 수 있도록 한다.
9. Visitor: 객체 구조를 이루는 원소에 대해 수행할 연산을 표현한다. 방문자는 연산에 적용할 원소의 클래스를 변경하지 않고 새로운 연산을 재정의할 수있다.
10. Chain of Responsibility: 요청을 처리하는 기회를 하나 이상의 객체에 부여하여 요청을 보내는 쪽과 받는 쪽의 결합을 피한다. 요청을 받는 객체를 연쇄적으로 객체를 처리할 수 있을 때까지 요청을 전달한다.

<br>



### Design Pattern vs Architecture vs Framework

Design Pattern이 실제 적용된 것이 Framework, 이를 바탕으로 실제 운영되는 SW로 구현한 결정체가 바로 Architecture이다. 핵심 코드는 Design Pattern을 바탕으로 구현된다.

| 구분        | Design Pattern                            | Architecture                           | Framework                            |
| ----------- | ----------------------------------------- | -------------------------------------- | ------------------------------------ |
| 품질 영향도 | 기능보다 주고, 가독성 및 향후 확장에 영향 | SW 최초 구조 결정, 최초 품질 평가 대상 | 반제품 형태, 도메인 종속적 품질 결정 |
| 구현체      | 미포함(샘플 제공)                         | 미포함(문서 제공)                      | 포함(코드 포함)                      |
| 도메인      | 독립적                                    | 독립적                                 | 종속적                               |
| 종류        | 생성, 구조, 행위                          | 다양한 Archetecture Style 존재         | Spring, Struts, Hibernate, ...       |



<br>
<br>



# Singleton Pattern

### Singleton Pattern이란?

Singletom Pattern을 따르는 클래스는 생성자가 여러 차례 호출되더라도 실제로 생성되는 객체는 하나이고 최초 생성 이후에 호출된 생성자는 최초의 생성자가 생성한 객체를 리턴한다. 이와 같은 디자인 유형을 **Singleton Pattern**이라고 한다. 주로 공통된 객체를 여러개 생성해서 사용하는 DBCP(DataBase Connection Pool)와 같은 상황에서 많이 사용된다.

![Singleton_UML_class_diagram](/Users/smy/Desktop/stack-img/Singleton_UML_class_diagram.svg)

<br>

### Singleton Pros-Cons

| Pros                                                         | Cons                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 하나의 인스턴스를 사용하여 메모리를 절약할 수 있다.<br>전역 인스턴스를 사용하여 다른 클래스의 인스턴스들이 데이터를 공유할 수 있다. | 인스턴스가 너무 많은 일을 하거나 많은 데이터를 공유하면 수정과 테스트가 어려워진다.<br>필요한 경우가 아니면 사용을 지양한다. |

<br>

### Singleton 사용처 및 예시 코드

* 사용처

  * 공통된 객체를 여러 개 생성해서 사용할 때
  * 전역에서 사용된 하나의 객체를 만들어야 할 때(ex) DBCP(Database Connection Pool), Logger)

* 예시 코드

  ![singleton](/Users/smy/Desktop/stack-img/singleton.jpeg)

```
public class SingletonPatternDemo {
  public static void main(String[] args) {

    // 항상 getter로 객체를 받음
    SingleObject object = SignleObject.getInstace();
  }
}
```

```
public class SingleObject {
  private static SingleObject instance = new SingleObject();

  // 생성자는 내부에서만 호출
  private SingleObject(){}

  // 외부에서 객체를 받아갈 수 있는 방법은 getInstance()가 유일
  public static SingleObject getInstance() {
    return instance;
  }
}
```



<br>

<br>



# Strategy Pattern

### Strategy Pattern이란?

Strategy Pattern(Policy Pattern)은 실행 중에 알고리즘을 선택할 수 있게 하는 Behavior Design Pattern이다.

간단하게 말해, 객체가 할 수 있는 행위 각각을 전략으로 만들어서 동적으로 행위의 수정이 필요한 경우 전략만 바꿔서 행위를 수정한다.

- 특정한 계열의 알고리즘들을 정의
- 각 알고리즘을 캡슐화
- 이 알고리즘들을 해당 계열 안에서 상호 교체가 가능하게 함

<br>

### Strategy Pros-Cons

| Pros                                                         | Cons                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 파생 클래스의 좋은 대안이다. 클래스를 상속하고 메소드를 오버라이팅하는 대신 단순 인터페이스만 구현하된 된다.<br>Context 객체를 필요로 하지 않으며, 특정 데이터에 집중할 수 있다.<br>시스템이 새로운 Strategy를 추가하기 쉽다.(= 다른 기능을 추가하기 쉽다.) 또한 기존 클래스들을 재컴파일하지 않아도 된다. | 통신 오버헤드가 클 수 있다. Strategy 객체에 전될된 인자의 일부가 사용되지 않을 수 있다.<br>사용되는 Strategy가 적다면 복잡성이 늘어난다. |

<br>

### Strategy 예시 코드

### ![strategy_pattern_uml_diagram](/Users/smy/Desktop/stack-img/strategy_pattern_uml_diagram.jpeg)

* Step 1) Strategy.java

```null
public interface Strategy {
   public int doOperation(int num1, int num2);
}
```

* Step 2) OperationAdd.java

```java
public class OperationAdd implements Strategy{
   @Override
   public int doOperation(int num1, int num2) {
      return num1 + num2;
   }
}
```

* Step 2) OperationSubstract.java

```
public class OperationSubstract implements Strategy{
   @Override
   public int doOperation(int num1, int num2) {
      return num1 - num2;
   }
}
```

* Step 2) OperationMultify.java

```
public class OperationMultiply implements Strategy{
   @Override
   public int doOperation(int num1, int num2) {
      return num1 * num2;
   }
}
```

* Step 3) Context.java

```
public class Context {
   private Strategy strategy;

   public Context(Strategy strategy){
      this.strategy = strategy;
   }

   public int executeStrategy(int num1, int num2){
      return strategy.doOperation(num1, num2);
   }
}
```

* Step 4) StrategyPatternDemo.java

```
public class StrategyPatternDemo {
   public static void main(String[] args) {
      Context context = new Context(new OperationAdd());		
      System.out.println("10 + 5 = " + context.executeStrategy(10, 5));

      context = new Context(new OperationSubstract());		
      System.out.println("10 - 5 = " + context.executeStrategy(10, 5));

      context = new Context(new OperationMultiply());		
      System.out.println("10 * 5 = " + context.executeStrategy(10, 5));
   }
}
```

* Step 5) output

```
10 + 5 = 15
10 - 5 = 5
10 * 5 = 50
```



<br>
<br>



# Template Method Pattern

### Template Pattern이란?

소프트웨어 공학에서 동작 상의 알고리즘의 프로그램 뼈대를 정의하는 Behavior Design Pattern

알고리즘의 구조를 변경하지 않고 알고리즘의 특정 단계들을 다시 정의할 수 있게 한다.

변하지 않는 기능은 슈퍼 클래스에 만들어두고 자주 변경하며 확장할 기능은 서브 클래스에서 만들어 사용한다.

<br>

### Template Method Pros-Cons

| Pros                                                         | Cons                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 코드의 중복 감소<br>자식 클래스의 역할을 감소시키면서 햄심 로직 관리에 용이<br>쉬운 객체 추가 및 확장 | 추상 메소드가 증가함에 따른 복잡한 클래스 관리<br>추상 클래스와 구현 클래스 같의 복잡성 증가 |

<br>

### Template Method 예시 코드

### ![template_pattern_uml_diagram](/Users/smy/Desktop/stack-img/template_pattern_uml_diagram.jpeg)

* Step 1) Game.java

```
public abstract class Game {
   abstract void initialize();
   abstract void startPlay();
   abstract void endPlay();

   //template method
   public final void play(){

      //initialize the game
      initialize();

      //start game
      startPlay();

      //end game
      endPlay();
   }
}
```

* Step 2) Cricket.java

```
public class Cricket extends Game {

   @Override
   void endPlay() {
      System.out.println("Cricket Game Finished!");
   }

   @Override
   void initialize() {
      System.out.println("Cricket Game Initialized! Start playing.");
   }

   @Override
   void startPlay() {
      System.out.println("Cricket Game Started. Enjoy the game!");
   }
}
```

* Step 2) Football.java

```
public class Football extends Game {

   @Override
   void endPlay() {
      System.out.println("Football Game Finished!");
   }

   @Override
   void initialize() {
      System.out.println("Football Game Initialized! Start playing.");
   }

   @Override
   void startPlay() {
      System.out.println("Football Game Started. Enjoy the game!");
   }
}
```

* Step 3) TemplatePatternDemo.java

```
public class TemplatePatternDemo {
   public static void main(String[] args) {

      Game game = new Cricket();
      game.play();
      System.out.println();
      game = new Football();
      game.play();		
   }
}
```

* Step 4) output

```
Cricket Game Initialized! Start playing.
Cricket Game Started. Enjoy the game!
Cricket Game Finished!

Football Game Initialized! Start playing.
Football Game Started. Enjoy the game!
Football Game Finished!
```



<br>
<br>



# Factory Method Pattern

### Factory Method Pattern란?

Factory method는 부모(상위) 클래스에 알려지지 않은 구체 클래스를 생성하는 패턴이며, 자식(하위) 클래스가 어떤 객체를 생성할지를 결정하도록 하는 패턴이기도 하다. (= 객체를 생성하기 위한 인터페이스를 정의한 후, 어떤 클래스의 인스턴스를 생성할지에 대한 처리는 서브 클래스가 결정한다.)

부모(상위) 클래스 코드에 구체 클래스 이름을 감추기 위한 방법으로도 사용한다.

객체 생성을 대신하주는 공장.

Factory 패턴에서는 생성 로직을 클라이언트에 노출시키지 않고 객체를 생성하고 공통 인터페이스를 사용하여 새로 생성된 객체를 참조한다.

<br>

### Factory Method Pros-Cons

| Pros                                                         | Cons                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 생성할 클래스를 미리 알지 못해도 Factory Class가 객체 생성을 담당<br>확장 용이성. 객체의 자료형이 하위 클래스에 의해서 결정<br> | 객체가 늘어날 때마다 하위 클래스 재정의로 인해 불필요한 클래스 생성 가능성 |

<br>

### Factory Method 예시 코드

![factory_pattern_uml_diagram](/Users/smy/Desktop/stack-img/factory_pattern_uml_diagram.jpeg)

* Step 1) Shape.java

```
public interface Shape {
   void draw();
}
```

* Step 2) Rectangle.java

```
public class Rectangle implements Shape {

   @Override
   public void draw() {
      System.out.println("Inside Rectangle::draw() method.");
   }
}
```

* Step 2) Square.java

```
public class Square implements Shape {

   @Override
   public void draw() {
      System.out.println("Inside Square::draw() method.");
   }
}
```

* Step 2) Circle.java

```
public class Circle implements Shape {

   @Override
   public void draw() {
      System.out.println("Inside Circle::draw() method.");
   }
}
```

* Step 3) ShapeFactory.java

```
public class ShapeFactory {
	
   //use getShape method to get object of type shape 
   public Shape getShape(String shapeType){
      if(shapeType == null){
         return null;
      }		
      if(shapeType.equalsIgnoreCase("CIRCLE")){
         return new Circle();
         
      } else if(shapeType.equalsIgnoreCase("RECTANGLE")){
         return new Rectangle();
         
      } else if(shapeType.equalsIgnoreCase("SQUARE")){
         return new Square();
      }
      
      return null;
   }
}
```

* Step 4) FactoryPatternDemo.java

```
public class FactoryPatternDemo {

   public static void main(String[] args) {
      ShapeFactory shapeFactory = new ShapeFactory();

      //get an object of Circle and call its draw method.
      Shape shape1 = shapeFactory.getShape("CIRCLE");

      //call draw method of Circle
      shape1.draw();

      //get an object of Rectangle and call its draw method.
      Shape shape2 = shapeFactory.getShape("RECTANGLE");

      //call draw method of Rectangle
      shape2.draw();

      //get an object of Square and call its draw method.
      Shape shape3 = shapeFactory.getShape("SQUARE");

      //call draw method of square
      shape3.draw();
   }
}
```

* Step 5) output

```
Inside Circle::draw() method.
Inside Rectangle::draw() method.
Inside Square::draw() method.
```



<br>

<br>



# MVC1 vs MVC2 Pattern

### MVC Pattern이란?

MVC 는 Model, View, Controller의 약자로, 하나의 애플리케이션, 프로젝트를 구성할 때 그 구성요소를 세가지의 역할로 구분한 패턴이다. (= 소프트웨어 디자인 패턴)

사용자가 controller를 조작하면 controller는 model을 통해서 데이터를 가져오고 그 정보를 바탕으로 시각적인 표현을 담당하는 View를 제어해서 사용자에게 전달한다.


| 구분       | 설명                                                         |
| ---------- | ------------------------------------------------------------ |
| Model      | - 어떤 동작을 수행하는 코드<br>- 순수 Public 함수로만 이루지며, 몇몇 함수들은 사용자 질의(query)에 대한 정보를 담는다. |
| View       | - Model은 여러 개의 View를 가질 수 있다.<br>- View는 Model에게 질의하여 Model로부터 값을 가져와 사용자에게 보여준다. (= 데이터 및 객체의 입출력을 담당)<br>- 사용자 인터페이스 요소로 사용자가 직접 볼 수 있는 화면을 의미한다. |
| Controller | - View는 여러 개의 Controller를 가진다.<br>- 프로그램의 작동 순서, 방식을 제어한다.<br>- 사용자는 Controller를 통해 Model의 상태를 변경하거나 다른 클래스에게 알릴 수 있는 함수가 필요하다. |



<br>

<br>



## 참고자료

Design Pattern의 개념과 종류

* https://ko.wikipedia.org/wiki/%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%EB%94%94%EC%9E%90%EC%9D%B8_%ED%8C%A8%ED%84%B4
* https://gmlwjd9405.github.io/2018/07/06/design-pattern.html

* https://coding-factory.tistory.com/708
* https://www.cisp.or.kr/archives/18726

Singleton Pattern

* https://ko.wikipedia.org/wiki/%EC%8B%B1%EA%B8%80%ED%84%B4_%ED%8C%A8%ED%84%B4
* https://dailyheumsi.tistory.com/149?category=855210
* 나중에 참고하면 좋을 자료: https://webdevtechblog.com/%EC%8B%B1%EA%B8%80%ED%84%B4-%ED%8C%A8%ED%84%B4-singleton-pattern-db75ed29c36

Strategy Pattern

* https://ko.wikipedia.org/wiki/%EC%A0%84%EB%9E%B5_%ED%8C%A8%ED%84%B4
* https://kscory.com/dev/design-pattern/strategy
* https://www.tutorialspoint.com/design_pattern/strategy_pattern.htm

Template Method Pattern

* https://ko.wikipedia.org/wiki/%ED%85%9C%ED%94%8C%EB%A6%BF_%EB%A9%94%EC%86%8C%EB%93%9C_%ED%8C%A8%ED%84%B4
* https://niceman.tistory.com/142
* https://www.tutorialspoint.com/design_pattern/template_pattern.htm

Factory Method Pattern

* https://ko.wikipedia.org/wiki/%ED%8C%A9%ED%86%A0%EB%A6%AC_%EB%A9%94%EC%84%9C%EB%93%9C_%ED%8C%A8%ED%84%B4
* https://www.tutorialspoint.com/design_pattern/factory_pattern.htm
* https://bamdule.tistory.com/157

