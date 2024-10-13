## Proxy
클라이언트가 사용하려고 하는 실제 대상인 것처럼 위장해서 클라이언트의 요청을 받아주는 역할을 한다.  

또한 클라이언트의 요청을 받아 원래 요청 대상에게 바로 넘겨주는 것이 아닌, 다양한 부가 기능을 지원할 수 잇다.  

- 타깃 : 최종적으로 요청을 위임받아 처리하는 실제 오브젝트


## 프록시 패턴
- 프록시 객체가 객체를 감싸서 클라이언트의 요청을 처리하도록 하는 패턴
- 접근 제어, 부가 기능 추가 등의 이유로 사용


### 스프링의 AOP
- 프폴기 기반의 AOP 구현체
- 스프링 빈에만 AOP 적용 가능
- 메서드 조인포인트 제공
- Runtime Weaving 방식

<img width="679" alt="image" src="https://github.com/user-attachments/assets/fc56f246-fce2-47e8-9cfd-e92d5a798c35">


- AOP 적용 전에는 DispatcherServlet에서 Controller로 요청을 넘긴다.
- AOP 적용 후에는 요청을 중간에 낚아챈다.
- AOP는 Dispatcher와 Controller 사이에서 실행된다.
- 대표적으로 @Transactional이 있다.
  - 쿼리 수행 전, setAutoCommit = false,
  - 쿼리 수행 후, commit or rollback 코드를 넣는다.
