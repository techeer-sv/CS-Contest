1.  **Spring이 하나의 HTTP 요청을 처리하는 과정을 순서대로 설명해주세요.**

- 1. 클라이언트가 Spirng에 HTTP 요청을 보냄
2. DispatcherServelt가 해당 요청을 우선적으로 받고 HandlerMapping에 요청을 보냄 
3. HandlerMapping은 URL과 매핑되는 Controller를  검색하고 DispatcherServlet에 결과를 반환합니다.
4. DispatcherServelt는 Controller의 알맞은 처리 요청을 HandlerAdapter에 보내면
5. HandelrAdapter가 해당 요청에 맞는 메소드를 Contorller에게 호출하고
6. Controller는 비즈니스 로직 처리 결과를 HandlerAdapter에게 반환합니다.
7. HandlerAdapter는 컨트롤러 실행 결과를 ModelAndView 객체로 변환 후 DispatcherServlet에게 반환하고
8. DispatcherServlet은 ModelAndView가 반환한 ModeAndView의 View 이름을 ViewResolver에게 검색을 요청하고
9. ViewResolver은 View 객체를 찾으면 반환, 없다면 생성하고 반환합니다.
10. DispatcherServlet는 View 객체에 Request Result 생성을 요청하고
11. View 객체는 클라이언트에게 Request Result를 Rendering 후 Client에게 응답합니다.

    <br> 
    
    1-1. **Spring 어플리케이션은 특정 endpoint에 대한 모든 사용자들의 요청을 하나의 controller로 처리합니다. 어떻게 가능한 걸까요?**
  - 답 : @RequestMapping, @GetMapping 등의 어노테이션을 이용해 URL 패턴에 따라 특정 메소드와 자동적으로 연결되어 특정 endpoint에 대한 모든 사용자의 요청을 처리합니다.

<br>

---
2. **DI, IoC, AOP, PSA에 대해 설명하고, Spring이 각각을 가져가는 이유에 대해 설명해주세요.**

- IOC는 외부에서 관리하는 객체를 가져와 사용하는 것인데 IOC를 구현하기 위해서는 DI가 필요합니다. 외부에서 관리하는 객체를 가져올 때 @Autowired 애너테이션을 사용해 빈을 주입하여서 스프링 컨테이너가 해당 객체를 관리하도록 구현하고, 다른 클래스에서 @Autowired를 통해 빈을 주입받으면 객체를 생성하지 않고 외부에서 사용할 수 있게됩니다.

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

- 원자성의 특징으로 트랜잭션이 롤백되고 실패로 처리 될 것 같습니다.

    <br>

    3-1. **`@Transactional(readOnly = true)`로 지정된 메서드 내에서 Dirty check가 동작할까요? 이유와 함께 설명해주세요.**

  - 답 : DirtyCheck는 엔티티 변경 여부를 확인하는데 readOnly = true는 엔티티가 변경될 수 없으므로 DirtyCheck는 동작하지 않을 것 같습니다.