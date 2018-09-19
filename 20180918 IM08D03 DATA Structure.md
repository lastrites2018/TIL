## checkpoint 3 this

```javascript
1. this는 arrow function 일 경우에만 lexicial

'this' means An object that the invoked function points to when executing.

2. 'this'는 window 
    -> function invocation, () 인 경우엔 bind를 하지 않는 이상은 보통 window


3. 
Look to the function in which it is defined
- that's what the context is bound to.
-> arrow function
에서의 this 설명. 
which(lexical 하다는 의미) arrow function을 사용한 함수는 '어디에서' 호출되는지만 고려해도 되기 때문.

5. window or the global object.
6. obj
7. window or the global object.
8. obj2, 
    obj.foo.call(obj2);
    call 나온 경우 앞뒤 안 보고 ()안만 보면 됨.

```

## free function invocation

```javascript
foo(); // function invocation
obj.foo(); // method invocation
```

-> free function invocation은 그냥  function invocation이라고 생각하면 됨.

## sprint review

생각하지 않을 경우엔 실수를 반복한다. 그래서 되돌아보는 과정이 필요하다. 



## Computer Programming

CPU는 연산.

Compile -> 기계어로 변환. -> 10101으로 한번 더 바꿈.

컴파일은 오래 걸림. embeded programming(C, 한정된 메모리에서 최적화하기 위해 애를 쓰게 됨)



---

## 

ES6 -> ES5 transfiler?

HL languages -> High-Level

기존 프로그래밍은 procedural languages 위에서 아래로 내려가는 식의 절차적인 언어(procedural Languages)



## OOP(Object-Oriented Languages) 

과거엔 웹 앱의 개념이 없었음

웹 사이트 - 정적static임

웹 앱 - 동적임dynamic

OOP는 확고한 무언가가 아니라 추상적인 프로그램 디자인 철학 같은 것

뭔가 하나의 틀을 만들자! - 객체!

기본적인 틀

class -> 자바스크립트는 결국 function인데, (function은 object니까??)

특징(property)과 액션(method)

static의 성질, 동적인 것 2가지로 나눔.

OOP의 컨셉?

알약? 클래스(메소드랑 밸류를 담은?)

자바스크립트는 외부에서 수정 가능

타입스크립트 이후 자바 세계가 달라짐

캡슐화를 잘 해놓으면 하나만 바꾸면 되는데, 아니면 전부 다 바꿔야 하니까 문제가 생김.

재사용성이 높아짐.

class 틀 instance는 object 틀로 찍은 object

```new DATE``` -> 여기서 DATE가 틀

추상화 ->OOP는 무대 뒤(내부)를 보여주지 않음. 입력과 결과만 보여줌.

다형성? 아빠 class의 Draw()메소드와 아들 클래스sub class에서 쓰는 메소드가 다를 수 있다. 상속 받았는데도. 어려운 개념. 

객체 지향은 추상적으로 대답하면 됨. 



## 알고리즘

알고리즘 : 논리

무작정 코딩하기보다, 뭘 물어보는지를 먼저 파악하고 서로 동의하는 것이 첫 걸음이 되어야 한다. 

슈도코드 : 스케치

중요한 건 전략이지, 문법이 아니다. 



시간

공간 - 부동산 개념



> 적절한 자료 구조를 선택하는 것이 좋은 알고리즘을 만들 수 있다



Queue : 줄 

선입선출. 먼저 들어오면 먼저 빠짐. (패스트푸드 줄 서기 생각)



>  과제에서 큐 구현시에 최적화는 신경쓰지 않고 구현한다



Stack : 프링글스

선입후출. (뒤에 들어온 애가 먼저 나감)

- 전자계산기
- 미로
- 컴퓨터 메모리 관리 (call, stack)



## checkpoint 4

```javascript
var obj1 = { x: 10 };
var obj2 = Object.create(obj1);
//object.create 되는 순간 별도의 영역이 되는 건가? 
obj2.x += 10;
obj1.x = 15;
// 이 시점에서 obj1  = { x : 15}; obj2 = { x : 20; }
var result = obj2.x;


// 틀린 문제

8번 - 다음 코드를 실행한 후, result 의 값은 무엇이 될까요?
var obj1 = { x: 10 };
var obj2 = Object.create(obj1);

var obj3 = Object.create(obj2);

obj2.x = 20;

var result = obj3.x + 10;

 result의 답은?

```





