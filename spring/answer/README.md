# Java & Spring

>  **자바(Java)**는 객체지향 프로그래밍 언어로서, 다양한 운영 체제에서 실행 가능한 플랫폼을 가지고 있어 많은 개발자들이 사용하고 있는 언어 중 하나입니다.
>
>  **스프링(Spring)**은 자바 기반의 프레임워크로서, 웹 애플리케이션을 개발하기 위한 다양한 기능을 제공합니다. 스프링은 다양한 모듈로 구성되어 있으며, 모듈들은 서로 연관되어 작동하도록 설계되어 있습니다. 



#### 1. JVM 구조

* **JVM이 무엇인가요?**

  > JVM은 Java Virtual Machine의 약자로 모든 자바로 작성된 프로그램을 실행시키기 위한 가상 머신입니다. 모든 자바 프로세스는 컴파일 후에 바이트  코드 형태로 JVM의 메모리에 적재되고 이후 실행 엔진의 Interpreter와 JIT 컴파일러에 의해 실행됩니다.
  >
  > [답변](https://velog.io/@jayl2sw/Java-Java%EC%99%80-JVMJava-Virtual-Machine)

* **JAVA의 컴파일 과정에 대해 설명해주세요.**

  > 1. 개발자가 자바 언어로 프로그램을 개발한다.
  > 2. .java 파일의 build를 진행한다 
  >    * `build`: 소스코드 파일을 실행 가능한 형태의 SW로 만드는 일련의 과정
  > 3. javac를 이용해 java로 작성된 파일을 바이트코드로 컴파일 한다.
  >    * 이 때, 생성된 바이트 코드는 컴퓨터가 바로 읽을 수 없고 JVM만 읽을 수 있다.
  > 4. 컴파일 된 바이트 코드를 Class Loader에 의해 JVM 내부로 로드
  > 5. Class Loader가 동적 로딩을 통해 필요한 클래스들을 로딩 및 링크하여 Runtime Data Area에 올림
  > 6. 실행 엔진은 JVM메모리에 올라온 바이트 코드들을 명령어 단위로 하나씩 가져와서 실행
  >
  > [답변](https://velog.io/@jayl2sw/Java-Java%EC%99%80-JVMJava-Virtual-Machine)

* **JVM의 메모리 구조에 대해서 설명해주세요.**

  > JVM 메모리 구조는 크게 모든 쓰레드가 공유하는 메모리 영역인 Method Area가 존재하며  객체 인스턴스들이 저장되는 Heap 영역, 각 스레드들이 
  >
  > [답변](https://velog.io/@jayl2sw/Java-Java%EC%99%80-JVMJava-Virtual-Machine)

* **JVM 내부에서 객체에 대한 참조가 진행되는 과정을 설명해주세요.**

* **JIT 컴파일러에 대해 설명해주세요.**

  > JIT 컴파일러는 Just-In-Time 컴파일러의 약어로, 런타임 시점에서 바이트 코드를 기계어로 컴파일 하는 컴파일러입니다. JVM은 프로그램을 처음 실행할 때, 인터프리터를 사용하여 바이트 코드를 실행합니다. 하지만 인터프리터는 빠른 실행 속도를 보장하지 않기 때문에, 프로그램이 실행되면서 자주 사용되는 코드를 JIT 컴파일러로 최적화하여 빠른 실행 속도를 보장할 수 있습니다.



<br>

#### 2. Garbage Collector(GC)

* **GC란 무엇인가요?**

  > 가비지 컬렉터는 Heap 영역의 효율성을 위해 자바에서 지원하는 기능으로 사용되지 않는 객체들을 식별하고 자동으로 메모리를 해제합니다. 이를 통해 개발자는 메모리 관리에 대한 부담을 덜 수 있습니다.

* **GC는 언제 수행되나요?**

  > Heap 영역은 크게 New Generation 영역과 Old Generation 영역으로 나누어집니다. 또, New Generation은 Eden 영역과 두개의 Survivor 영역으로 나뉘어집니다. 처음 생성되는 객체는 Eden 영역에 생성되며 

* **Heap 영역에서 제거 대상을 탐색하는 방법을 설명해주세요.**

* **Java에서 사용되는 GC의 종류 등을 설명해주세요.**



<br>

#### 3. **원시타입**

* **자바의 6가지 원시타입에 대해 설명해주세요.**
* **Wrapper Class가 무엇인가요?**
* **python은 모든 원소를 객체로 두는 반면 Java는 원시타입을 제공합니다. 원시타입을 왜 존재하나요?**



<br>

#### 4. Interface vs Abstract Class

* **인터페이스와 추상클래스의 차이점에 대해서 설명해주세요.**
* **왜 자바에서는 클래스간의 중복 상속을 허용하지 않나요?**



#### 5. Reflection

* **reflection에 대해 설명해주세요.**
* **reflection을 언제 활용할 수 있을까요?**
* **프레임워크 또는 라이브러리는 왜 일반적으로 기본 생성자를 요구하나요?**
* **리플렉션의 단점을 설명해주세요.**



#### 6. Exception

* **Exception과 Error의 차이를 설명해주세요.**

* **예외처리를 하는 세 방법에 대해 설명해주세요.**
* **CheckedException, UncheckedException의 차이에 대해 설명해주세요.**
* **예외 처리에 오버헤드가 많이 발생하나요?**



<br>

#### 7. Stream

* **Stream에 대해 설명해주세요**
* **Stream과 for ~ loop의 성능 차이를 비교해주세요**



<br>

#### 8. Java & Spring

* **사용하는 Java와 Spring 버전을 말하고 해당 버전의 특징을 말해주세요**
* **stream과 lambda에 대해 설명해주세요.**
* **Spring을 사용하는 이유에 대해서 설명해주세요 (POJO와 Servlet을 이용하는 것과 비교해 장점)**



<br>

#### 9. IoC & DI

* **IoC와 DI에 대해서 설명해주세요.**
* **Spring에서는 어떻게 DI를 구현하고 있나요?**
* **Spring의 Bean의 생성 주기에 대해 설명해주세요.**
* **프로토타입 빈은 무엇인가요?**



<br>

#### 10. Spring MVC 구조

* **Spring MVC 구조에 대해 설명해주세요.**



<br>

#### 11. AOP

* **AOP에 대해서 설명해주세요.**
* **@Aspect의 동작 방식을 설명해주세요.**
* **Spring에서는 AOP를 어떻게 구현하고 있나요?**
* **JDK Proxy와 CGLIB의 차이점은 무엇인가요?**
* **자신이 AOP를 사용한 경험을 말해주세요.**



<br>

#### 12. Transactional

* **@Transaction이 하는 역할을 알려주세요**
* **읽기에 Transaction(readonly=true)를 하는 이유가 있을까요?**



<br>

#### 13. Interceptor & Servlet Filter

* **Interceptor와 Servlet Filter의 차이점에 대해 말해주세요.**
* **그럼 각각이 왜 분리되어 있는지 설명해주세요.**



<br>

#### 14. JPA

* **JPA과 같은 ORM을 사용하는 것이 무엇인가요?**
* **N+1 문제에 대해 설명해주세요**
* **영속성은 어떤 기능을 하나요?**



<br>

#### 15. 

#### 16. Unit Test



