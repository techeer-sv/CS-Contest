1.  **Spring이 하나의 HTTP 요청을 처리하는 과정을 순서대로 설명해주세요.**

- 답 :
1. HTTP 요청 (DispatcherServlet에서 HTTP 요청 확인)
2. DispatcherServlet에서 컨트롤러로 HTTP 요청 위임
3. 컨트롤러 — 모델 생성 및 모델 (Map)에 값 저장
4. 생성한 모델과 사용할 뷰 정보 전달
5. DispatcherServlet 뷰 생성 요청
6. 뷰 작업을 통해 응답 데이터 생성 (이 때 뷰 오브젝트에서 생성한 모델 객체 참조)
7. HTTP 응답 (서블릿 컨테이너가 서블릿이 생성한 응답 값을 클라이언트에 전송)

    <br> 
    
    1-1. **Spring 어플리케이션은 특정 endpoint에 대한 모든 사용자들의 요청을 하나의 controller로 처리합니다. 어떻게 가능한 걸까요?**
  - 답 : DispatcherServlet은 Servlet WebApplicationContext을 포함하고 있습니다.

`Spring` 에서 제공한 `DispatcherServlet` 이 서블릿 컨테이너에 의해 초기화 될 때 서블릿 레벨의 `Servlet WebApplicationContext` 를 생성하고, `DispatcherServlet` 의 `Servlet WebApplicationContext` 에 대한 디폴트 설정을 기준으로 컨텍스트를 구성합니다.

디폴트 설정을 기준으로 여러 웹 프레젠테이션 계층의 컴포넌트들이 이 곳에 저장되고, 그리고 위에서 질문 했던 `컨트롤러` 역시 이 곳에 위치한 것을 확인 할 수 있습니다.

 Servlet WebApplicationContext 내에는 HandlerMapping 클래스도 존재하는데 해당 클래스를 상속하는 `RequestMappingHandlerMapping` 를 통해서 설정합니다.

Controller 클래스 위에 @RequestMapping 을 표시하면 어노테이션을 확인하고 `RequestMappingHandlerMapping`을 만들어 DispatcherServlet에 등록하기 때문에 **특정 endpoint에 대한 모든 사용자들의 요청을 하나의 controller로 처리가 가능합니다.**

<br>

---
2. **DI, IoC, AOP, PSA에 대해 설명하고, Spring이 각각을 가져가는 이유에 대해 설명해주세요.**

- 답 :

**DI**

- 종속성 주입은 클래스의 종속성이 클래스 자체 내에서 생성되지 않고 외부에서 주입되는 디자인 패턴입니다.

**Spring이 DI를 사용하는 이유**

Spring 은 생성자, setter 또는 메서드를 통해 종속성을 주입하여 결합도를 낮추고 좀 더 유연한 코드를 만드는 것을 지향하는데 이를 통해 코드의 재활용성을 높여 유지보수가 용이해지고, 단위 테스트하기가 더 쉬워지기 때문입니다.

**IoC**

- 종속의 흐름과 인스턴스화를 직접 제어하는 구성 요소 대신 제어가 외부 프레임워크나 컨테이너로 전환된 것을 말한다.

**Spring이 IoC를 사용하는 이유:** Spring의 IoC 컨테이너는 Bean(구성 요소)의 라이프 사이클과 해당 종속성을 관리합니다. 애플리케이션 내에서 수동 인스턴스화 및 제어 흐름이 필요하지 않으므로 더욱 모듈화되고 확장 가능해집니다.

**AOP**

- AOP는 개발자가 핵심 비즈니스 로직에서 교차 관심사(예: 로깅, 보안)를 분리하여 모듈화할 수 있도록 하는 프로그래밍 패러다임

**Spring이 AOP를 사용하는 이유:** Spring은 AOP를 통합하여 개발자가 애플리케이션의 핵심 로직에서 로깅, 보안 및 트랜잭션 관리와 같은 문제를 분리할 수 있도록 합니다. 

**PSA**

PSA는 프레임워크가 다양한 기술로 구현할 수 있는 인터페이스 또는 추상화 집합을 제공하여 코드를 기본 구현과 독립적으로 만드는 접근 방식입니다.

**Spring이 PSA를 사용하는 이유:** Spring의 PSA를 사용하면 데이터베이스, 메시징 시스템 및 트랜잭션 관리와 같은 다양한 기술에 대한 일관된 추상화 세트를 제공할 수 있습니다. 이를 통해 개발자는 애플리케이션 코드를 변경하지 않고도 구현 간에 원활하게 전환할 수 있습니다. 예시로는 데이터베이스 JDBC 템플릿이 있습니다.

<br>

---
3. **아래 코드에서 `makeAccount(account)`가 실패했을 때 `register 메서드`의 실행 결과를 추론하고, 해당 결과가 가능한 이유를 최대한 자세하게 설명해주세요.**

    ```java
    
    @Transactional
    public void register(User user) {
    	userRepository.save(user);	
    	makeAccount(account);
    }
    
    @Transactional
    public void makeAccount(User user) {
    	Account account = new Account(user);
    	accountRepository.save(account);
    }
    ```

- 답 : 

    <br>

    3-1. **`@Transactional(readOnly = true)`로 지정된 메서드 내에서 Dirty check가 동작할까요? 이유와 함께 설명해주세요.**

  - 답 : 
