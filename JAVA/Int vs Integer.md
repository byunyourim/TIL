# int 와 Integer 

### int
- Primitive 자료형으로 변수의 타입(data type)이다

    >Primitive
    >- 데이터를 가지는 자료형을 뜻하는 원시적이 자료형.
    >- 메소드를 가지지 못한다.
 

앞서 변수의 타입으로 표현하였는데. 변수는 값을 저장할 수 있는 메모리 상의 공간을 의미한다.<br>

 
```
int a = 3;    // a : 변수

char firstName = "H";   // firstName : 변수
```

int와 char처럼 변수의 형을 지정해주는 것을 변수의 타입(data type)이라고 한다.<br>
 
즉, 자료형은 `data의 type에 따라 값이 저장될 공간의 크기와 저장 형식을 정의한 것` 이라고 볼 수 있다.<br>
<br>

### Integer
- int 자료형을 객체로 다루기 위한 클래스 (wrapper class)<br>

  > 래퍼 클래스(wrapper class)<br>
  > 객체가 기본 데이터 유형을 래핑하거나 포함하는 클래스<br>
  > 래퍼 클래스를 이용하면 객체를 만들 때 필드를 포함하고 이 필드에 기본 데이터 유형을 저장할 수 있다.


##### 기본형을 객체로 다룬다는 것은 어느 경우를 말하는걸까❓
- 매개변수로 `객체`를 필요로 할 때
- 기본형 값이 아닌 `객체로 저장`해야할 때
- `객체 간 비교`가 필요할 때

- Integer 클래스의 목적은 단일 int 값을 추적하는 것이므로 Integer 클래스는 내부적으로 단일 값을 유지한다.

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
- ###### 산술 연산 가능
- ###### null 로 초기화 불가능
- ###### 저장공간이 4byte
- ###### == 로 비교
- ###### 메서드 사용 불가<br>
<br>

#### Integer
- ###### 객체이기 때문에 Unboxing 하지 않을 시 산술 연산 불가능
- ###### 기본형을 Wrapper class로 감싸기 때문에 **null 값 처리가 가능**하다 
- ###### 저장 공간이 큼
- ###### null 값으로 처리가 가능해 SQL에 용이
- ###### .equals로 비교
- ###### 메서드 사용 가능<br>
 <br>

### 언제 사용할까?
int를 사용하는 것이 계산 속도와 메모리 측면에서 이점이 있다 <br>

#### 그럼 Integer는?

###### **null 또는, 데이터를 wrapper 할 경우**에 사용한다.
