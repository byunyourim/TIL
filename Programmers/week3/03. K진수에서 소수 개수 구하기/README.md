## 문제 이해하기

<br><br>

## 재정의
n -> k진법 변환
0으로 자르기

소스의 개수 찾기

<br><br>

## 알고리즘
시간복잡도 : O(N)

<br><br>

## 의사코드
count 소수의 개수
value = Integer.toString(n, k) 진법변환한수

int[] numbers = value를 0으로 자른 배열
for (number : numbers) {
    소수인지 확인
    if (소수인경우) count++;
}
count 반환

<br><br>

## 구현
