

## 공인 IP
- 전 세계에서 유일한 IP 주소
- ISP(인터넷 서비스 제공자)가 인터넷에 연결된 장치에 할당
- 인터넷을 통해 전 세계와 직접 연결될 수 있음


<br>


## 사설 IP
- 로컬 네트워크(가정, 회사 등)에서만 사용되는 IP 주소
- 여러 네트워크에서 중복 사용 가능(다른 집이나 회사에서도 같은 사설 IP 사용 가능)
- 인터넷에 직접 연결되지 않고, 공인 IP를 통해 인터넷에 연결됨


<br>


## 왜 사설 IP를 사용하는지
### 1. IPv4 주소 부족 문제 
IPv4 주소는 32비트로 표현되며, 약 43억 개의 주소만 제공할 수 있다.   
인터넷 사용자와 장치의 수가 급격하게 늘어나며 공인 IP 주소가 복잡해졌다.  

사설 IP는 로컬 네트워크 안에서만 사용되기 때문에,   
공인 IP 주소를 낭비하지 않고 여러 가정이나 회사에서 중복으로 사용할 수 있다.  

<br>

### 2. 보안 강화
사설 IP는 인터넷 외부에서 직접 접근할 수 없다. 그래서 네트워크 보안에 좋다. 
예를 들어, 가정 내의 컴퓨터에 할당된 사설 IP는 외부에서 접근할 수 없기 때문에, 외부 공격자가 쉽게 침투할 수 없다.
즉, 사설 IP는 인터넷 외부로부터의 불필요한 접근을 차단하는 방패 역할을 한다.

<br>

### 3. 효율적인 네트워크 관리
사설 IP는 로컬 네트워크 내에서 장치들을 식별하고 관리하는 데 사용된다.  
예를 들어, 집에서 프린터를 사용하거나 다른 기기와 파일을 공유할 때 사설 IP를 사용한다.  
공인 IP는 인터넷을 통해 장치를 식별하지만, 사설 IP는 로컬 네트워크 내에서 그 역할은 한다.



<br><br><br>

## 사설 IP와 공인 IP의 동작
1. 집에 라우터가 있고, 이 라우터는 ISP로부터 하나의 공인 IP를 할당받는다.
2. 집 안에 있는 컴퓨터, 스마트폰, 스마트 TV는 각각 라우터로부터 사설 IP를 할당받는다.
3. 이 장치들은 라우터를 통해 인터넷에 연결되는데, 라우터는 NAT 기능을 통해 하나의 공인 IP로 여러 장치가 인터넷에 나갈 수 있도록 해준다.





<br><br><br>


사설 IP는 공인 IP 자원을 절약하고, 네트워크를 안전하게 보호하며, 로컬 네트워크에서 장치 간의 통신을 관리하는 데 사용됩니다.
공인 IP는 인터넷 상에서 장치를 식별하고, 사설 IP는 로컬 네트워크 내에서 장치를 식별합니
