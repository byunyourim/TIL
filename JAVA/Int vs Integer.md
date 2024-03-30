# int 와 Integer 

### int
- Primitive 자료형으로 변수의 타입(data type)이다

    >Primitive
    >- 데이터를 가지는 자료형을 뜻하는 원시적이 자료형.
    >- 메소드를 가지지 못한다.
 

앞서 변수의 타입으로 표현하였는데. 변수는 값을 저장할 수 있는 메모리 상의 공간을 의미한다.<br>

 
```
int a = 3;

char firstName = "H";
```
a와 firstName은 변수이다.<br>

int나 char가 처럼 변수의 형을 지정해주는 것을 변수의 타입(data type)이라고 한다.<br>
 
즉, 자료형은 `data의 type에 따라 값이 저장될 공간의 크기와 저장 형식을 정의한 것` 이라고 볼 수 있다.<br>
<br>

### Integer
- int 의 Wrapper class<br>

 > 래퍼 클래스(wrapper class)<br>
  > 객체가 기본 데이터 유형을 래핑하거나 포함하는 클래스<br>
  > 래퍼 클래스를 이용하면 객체를 만들 때 필드를 포함하고 이 필드에 기본 데이터 유형을 저장할 수 있다.


##### 기본형을 객체로 다룬다는 것은 어느 경우를 말하는걸까❓
- 매개변수로 객체를 필요로 할 때
- 기본형 값이 아닌 객체로 저장해야할 때
- 객체 간 비교가 필요할 때

```
ArrayList<Integer> intList = new ArrayList<Integer>();
intList.add(1);
intList.add(2);
System.out.println(intList.get(0));
String stringNum = "123";
int intNum = Integer.parseInt(stringNum);
System.out.println(intNum);
```


### int 와 Integer의 차이
#### int
- 자료형으로 산술 연산 가능
- null 로 초기화 불가능
- 저장공간이 4byte<br><br>

#### Integer
- Unboxing 하지 않을 시 산술 연산 불가능
- **null 값 처리 가능**
- 저장 공간이 큼
- null 값으로 처리가 가능해 SQL에 용이<br>
 <br>

### 언제 사용할까?
프로그램에 무리가지 않기 위해 보통 int를 사용한다. <br>
용량이 더 작고 null값이 들어오지 못하니 값이 없을 땐 에러를 발생.

그럼 Integer는?

**null 또는, 데이터를 wrapper 할 경우**에 사용한다.
