1.  **Spring이 하나의 HTTP 요청을 처리하는 과정을 순서대로 설명해주세요.**

- 답 : 

    <br> 
    
    1-1. **Spring 어플리케이션은 특정 endpoint에 대한 모든 사용자들의 요청을 하나의 controller로 처리합니다. 어떻게 가능한 걸까요?**
  - 답 :

<br>

---
2. **DI, IoC, AOP, PSA에 대해 설명하고, Spring이 각각을 가져가는 이유에 대해 설명해주세요.**

- 답 : 

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