## AOP
애플리케이션은 핵심기능과 부가 기능으로 구성된다.  

부가기능은 여러 곳에서 반복된다.  

AOP는 부가기능을 하나의 Aspect로 보고 적용, 수정, 관리를 한 곳에서 수행하는 것이다.  

즉, 여러 곳에서 적용할 수 있는 코드를 하나 곳에서 관리하여 모듈화한다.  

<img width="683" alt="image" src="https://github.com/user-attachments/assets/1187364a-904b-41ff-b5d3-5fb165c4823e">




<br>  

스프링은 프록시 방식의 AOP를 사용한다.  

@AOP와 포인트컷을 통해 직접 AOP를 만들 수 있다.  

스프링이 제공하는 AOP에는 대표적으로 @Transactional이 있다.  


### 프록시 AOP의 동작 방식
<img width="686" alt="image" src="https://github.com/user-attachments/assets/4140f110-e94e-4c67-9299-b29c9ed55391">

- @Transactional이 붙은 메서드를 포함한 클래스의 프록시 객체를 생성한다.
- 프록시 객체 내부에서 트랜잭션과 관련된 모든 로직을 처리한다.
- 트랜잭션과 관련 없는 순순한 핵심 로직은 실제 객체를 호출하여 처리한다.



프록시 방식이 AOP는 프록시 객체를 통해 메서드가 호출된다.  
- 프록시를 거치지 않고 대상 객체를 직접 호출하게 되면 AOP가 적용되지 않고, Advice도 호출되지 안흔다.
- 즉, 메서드 호출이 프록시 객체를 통해서 전달될 때 AOP가 적용된다.
- 클래스 내부에서 자기 자신의 메서드를 호출하는 경우(내부 호출),
  프록시 객체를 경유하지 않고, 자기 자신의 인스턴스를 직접 호출하는 방식으로 처리되기 때문에 AOP가 적용되지 않느다.


스프링에서 AOP는 프록시 객체를 통해 메서드 호출을 가로채고, 이 과정에서 필요한 부가 작업(Advice)을 적용한다.  
하지만 내부 호출을 하게 되면, 프록시 객체가 아닌 본인 객체의 메서드를 직접 호출하는 것이 되기 때문에 AOP 적용의 기회가 사라지는 것이다.  

프록시 객체는 외부에서 해당 빈을 호출할 때 동작한다.    
외부에서 해당 메서드가 호출되면 스프링의 프록시가 가로채서 AOP를 적용하지만, 같은 클래스 내에서 호출하는 경우 프록시 객체를 통하지 않기 때문에  
AOP가 적용되지 않는다.  

#### 해결
1. 자기 자신 의존성 주입
  - 자기 자신의 인스턴스를 스프링 빈으로 주입받아 사용ㅎ나다.
  - 이렇게 하면 자기 자신의 메서드를 호출할 때 프록시 객체를 통해 호출되기 때문에 AOP가 적용된다.
```java
@Component
public class MyService {

    @Autowired
    private MyService myService;  // 자기 자신의 빈 주입

    @Transactional
    public void transactionalMethod() {
        // 트랜잭션 로직
    }

    public void externalMethod() {
        // 프록시 객체를 통해 AOP 적용
        myService.transactionalMethod();
    }
}
```
주입받은 자신을 통해 메서드를 호출한다.  

하지만, 위의 방법은 순환 참조 문제가 발생할 수 있다.  

<br>

2. 지연 조회
   - ObjectProvider 또는 ApplicationContext를 사용하여
     실제 객체 사용 시점에 스프링 빈을 조회하는 방식이다.
```java
@Component
public class MyService {

    private final ObjectProvider<MyService> myServiceProvider;

    public MyService(ObjectProvider<MyService> myServiceProvider) {
        this.myServiceProvider = myServiceProvider;
    }

    @Transactional
    public void transactionalMethod() {
        // 트랜잭션 로직
    }

    public void externalMethod() {
        // 실제 호출 시점에 빈을 조회하여 프록시 객체를 통해 메서드 호출
        myServiceProvider.getObject().transactionalMethod();
    }
}
```
필요한 시점에 빈을 조회하는 방법이다.  
ObjectProvider는 지연된 빈 조회를 가능하게 한다. 하지만, 지연된 객체 접근으로 이해 성능 이슈가 있을 수 있다.   

<br>
4. 구조 변경
   - 클래스를 분리한다. 
   기능을 여러 클래스로 분리하여 내부 메서드 호출을 피한다.  
   AOP가 필요한 메서드를 별도의 클래스로 옮기고, 그 클래스를 호출하는 방식으로 구조를 변경한다.  
```java
@Component
public class MyService {

    private final MyOtherService myOtherService;

    public MyService(MyOtherService myOtherService) {
        this.myOtherService = myOtherService;
    }

    public void externalMethod() {
        // 다른 클래스의 메서드를 호출
        myOtherService.transactionalMethod();
    }
}

@Component
public class MyOtherService {

    @Transactional
    public void transactionalMethod() {
        // 트랜잭션 로직
    }
}
```
코드 구조의 변화가 크며, 클래스 간 의존성이 늘어날 수 있다.





   
