키와 값이 1:1로 연관지어 저장되는 자료구조로 키를 이용하여 값을 도출한다.  

<br>  

키는 고유한 값으로 저장 공간의 효율성을 위해 해시 함수에 입력하여 해시로 변경 후 저장된다.
그 이유는 키는 길이가 다양하기 때문에 그대로 저장하면 다양한 길이만큼 저장소의 구성이 필요하기 때문이다.  
  
해시함수는 키를 해시로 바꿔주는 역할을 하며 해시 충돌이 발생할 확률을 줄여주는 함수를 만드는 것이 중요합니다.

해시는 해시함수의 결과로 저장소에서 value와 매칭되어 저장됩니다.

value는 저장소에 최종적으로 저장되는 값으로 키와 매칭되어 저장, 삭제, 검색, 접근이 가능합니다.

해시함수를 통해 얻은 해시값을 배열의 인덱스로 사용하여 해당 인덱스에 밸류값을 저장합니다.



<br>


### 해시충돌
서로 다른 키가 해시 함수에서 동일한 해시를 반환하는 경우를 말한다. 충돌이 많아질수록 탐색의 시간 복잡도가 O(1)에서 O(n)으로 증가한다.



<br>

### 장점
해시 테이블의 장점으로는 작은 리소스로 많은 데이터를 효율적으로 관리할 수 있다.  
또한 배열의 인덱스를 사용하기 때문에 빠른 검색, 삽입, 삭제가 가능하며, 키와 해시에 연관성이 없어 보안에 유리한다.  
중복제거에 유용합니다.


<br>


### 단점
단점으로는 충돌이 발생할 가능성이 있으며, 충돌 발생시 공간 복잡도가 증가한다.   
또한 순서가 없으며 해시함수에 의존할 수 밖에 없다.


<br>

### HashTable vs HashMap
- Key-Value 구조 및 Key에 대한 Hash로 Value 관리하는 것은 동일
- HashTable
  - 동기
  - Key-Value 값으로 null 미허용 (Key가 hashcode(), equals()를 사용하기 때문)
  - 보조 Hash Function과 separating Chaining을 사용해서 비교적 충돌 덜 발생 (Key의 Hash 변형)
- HashMap
    - 비동기 (멀티 스레드 환경에서 주의)
    - Key-Value 값으로 null 허용
 

<br>

### HashTable 성능
  
|  | 평균 | 최악 |
| --- | --- | --- |
| 탐색 | O(1) | O(N) |
| 삽입 | O(1) | O(N) |
| 삭제 | O(1) | O(N) |
