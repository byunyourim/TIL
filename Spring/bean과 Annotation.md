## Spring Bean
POJO로써 Spring 애플리케이션을 구성하는 핵심 객체로, Spring IoC컨테이너에 의해 생성, 관리된다.  
class, id, scope, constructor-arg등을 주요 속성으로 갖는다.  

bean은 클래스의 인스턴스이다.  

@Component, @Service, @Repository, @Configuration와 같은 어노테이션이 붙은 클래스는 Spring의 IoC 컨테이너에 의해 관리된다.  

이 클래스의 인스턴스가 생성되면 Bean으로 등록된다.  

@Component나 @Configuration와 같은 어노테이션이 붙은 클래스는 스프링이 관리할 대상이다.  

애플리케이션이 시작될 때 스프링 IoC 컨테이너가 해당 클래스를 스캔하여 인스턴스를 생성하고, 빈으로 등록한다.  

빈은 ApplicationContext에 등록되며, 등록된 인스턴스는 애플리케이션 전역에서 사용할 수 있는 빈이 된다.  


#### 어노테이션을 사용해서 빈을 생성하는 방법
1. @Configuration, @Bean을 사용해 빈 설정 정보 클래스를 생성한다
2. @Component와 이를 상속한 @Repository, @Controller어노테이션 등을 사용해 자바 컴포넌트를 생성한다.


### @Configuration
- 스프링 IOC Container에게 해당 클래스를 Bean 구성 클래스임을 알려주는 어노테이션
- java 클래스를 이용하여 스프링 빈과 설정을 정의할 수 있도록 한다.
- 



```java
@Configuration
public class Config {

    @Bean
    public MyBean myBean() {
        return new MyBean();
    }
}
```
```java
// 빈으로 등록한 클래스
public class MyBean {

    public void sayHello() {
        System.out.println("hello~");
    }
}
```

ApplicationContextt는 @Configuration이 붙은 클래스 내부에서 @Bean이 붙은 메서드를 찾는다.  
- @Bean이 붙은 메서드들은 자바 객체들을 반환하는 메서드이다.
- 반환된 자바 객체는 스프링 컨테이너에 빈으로 등록된다.
- 빈의 이름은 @Bean이 붙은 메서드 이름이 된다. (위의 코드의 경우 메서드명과 같은 myBean이 생성된다.)

<br>

### @Bean
- 메서드 레벨의 어노테이션으로 인스턴스화하는 코드가 수동으로 작성된다.
- 개발자가 직접 제어 불가능한 외부 라이브러리 등을 Bean으로 만들려고 할 때 사용된다.

<br>

### @Component
개발자가 직접 작성한 클래스를 Bean으로 동록하기 위한 어노테이션

<br>

### @Autowired
- 의존성을 자동으로 주입하는 어노테이션
- 
<br>

### @Aspect
- 해당 클래스가 부가 기능 클래스임을 알려주는 어노테이션이다.
- 따로 빈으로 등록해주는 작업이 필요하다.
  
<br>

### @Around("Pointcut")
- Advice의 한 종류로 핵심 관심사의 실패 여부와 관계 없이 전 후로 실행되도록하는 Advice이다.
- 지정된 패턴에 해당하는 메서드가 실행되기 전, 후 모두 동작한다.
- 이 어노테이션이 붙은 메서드의 반환 값은 Object여야 한다.
- 
<br>

### @Pointcut
- 부가 기능이 적용될 JoinPoint를 정의한 것
