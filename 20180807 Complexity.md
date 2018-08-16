## Complexity Analysis In the Real World

컴퓨터 사이언스에서 배우는 이슈

필요성 

1. 좋은 코드
2. 효과적인 코드



time and space

//얼마나 빨리? 얼마나 공간(메모리)?



## 왜 중요한가

효과적인 알고리즘이 뭔지, 효과적인 데이터 스트럭처가 뭔지. 



접근방법이 다르다는 게 focus



배열은 순서가 있지만,

객체는 순서가 없다!



객체는 순차적으로 iteration 하는게 의미가 없다

tuple, rankedlist(블록체인), q, stack 등 다양한 데이터 구조. 



어떤게 효과적인지 알아보기 위해 측정하는 기준이 바로 complexity



> 사이즈가 모든 시간을 대표하진 않는다



Big - O Notation

근사값

Complexity Types

O(1) O(log n) O(n) O(n제곱) O(c")

상수의 제곱으로 가면 정말 느려짐

근사값이기 때문에 n제곱 뒤에 붙는 덧셈 따위 무시함.

Hash table은 object라고 생각하면 됨 



constant O(1) 1의 복잡도

ARRAY LOOKUP : 알고 있는 인덱스를 가지고 접근하는 것 

HASH TABLE INSERTION



logarithmic O(log n) Example : BINARY SEARCH

  divide and conquer : recursion

* 알아둘 필요가 있다

log n 번만큼 돔 3번

element가 7개 바이너리 연산 3번

Math.log2(7)

2.8 -> 3번

무작정 늘어나는게 아니라 log n만큼의 복잡도



linear O(n)

PRINTING the elements in an array

모든 엘리먼트 탐색



quadratic O(n제곱)

CONSTANT  TIME OPERATION INSIDE TWO NESTED FOR -LOOPS

중첩 for 문



exponential

O(c의 n제곱)

Excution time increaes exponentially

-> 패스워드 추적하기 힘들게 만들때



> 내가 구현한 것이 어떠한 복잡도를 가진지 알아야 한다



complexity cheat sheet

http://bigocheatsheet.com/

데이터 자료 구도 보고 어떻게 알아보는지도 볼 필요가 있다


