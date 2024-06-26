나는 이전 회사에서 웹 개발을 할 때 JSP 와 JSTL 을 사용했다.


그런데 이번에 스프링 부트를 공부하면서 thymeleaf 를 처음 들었다

너무 늦은 감이 있지만 둘의 차이를 알아보자..


## JSP 
html 파일이 아닌 **자바 파일** 로 프론트와 백의 구분이 명확하지 않을 수 있다.

- 서블릿 기술의 확장
- 유지 관리가 용이
- 빠른 개발이 가능

JSP 를 사용하면 Web Application 배포시 WAR 파일로 생성이 되는데 이것은 압축타입으로 Servlet 해석과 관련된
모든 패키지를 포함시키면서 복잡하고 무거운 구조이다.


그리고 자바코드를 태그안에 직접 작성할 수 있으나 최대한 사용하지 않는 것이 좋다.

또한 JSP 의 경우 서버를 통해 열어야 정상적으로 확인이 가능하다



이에 반해



## 타임리프 (Thymeleaf)

스프링 부트에서 공식적으로 지원하는 뷰 템플릿 엔진

순수 html 구조이며 서버 구동없이 직접 웹 브라우저를 열어 HTML 파일의 내용을 확인할 수 있다

서버를 거친다면 동적인 페이지를 구현할 수 있다.

-> 서버 사이드 렌더링


그러면 타임리프는 어떻게 순수 HTML파일을 유지하면서 동적 HTML 파일을 제공할 수 있을까? 



간단하게 서버 가동없이 웹 브라우저를 이용해 해당 파일을 열게 되면 웹 브라우저는 타임리프가 사용하는 속성인 th:속성을 알지 못하기 때문에
타임리프 속성을 제외한 순수 HTML 속성으로 화면을 구성하여 순수 HTML파일을 유지할 수 있다.


반면에 서버가 가동이 되어 타임리프 뷰 템플릿 엔진을 이용하게 되면 서버 사이드에서 렌더링 되어
기존 HTML의 속성이 아닌 타임리프의 속성으로 대체되어 동적 HTML 파일을 제공할 수 있게된다.

