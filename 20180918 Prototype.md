## Prototype을 이해해보자

객체는 언제나 함수 (Function)로 생성된다.

```javascript
function Person () {}  // -> 함수(f부터 }까지의 문자열이 )
var personObject = new Person(); // 함수로 객체 생성
```

personObject는 Person이란 함수로 생성된 객체. 

```javascript
var obj = {};
// 위 코드와 동일
var obj = new Object();


```

> object도 함수다! Object를 console 창에서 쳐보면 함수로 나옴. 



**함수가 정의될 때는 2가지 일이 동시에 이루어짐**

1. 해당 함수에 Constructor (생성자) 자격 부여

Constructor 자격이 부여되면 new를 통해 객체를 만들어 낼 수 있게 됨. 이것이 함수만이 new 키워드를 사용할 수 있는 이유다. constructor가 아니면 new를 사용할 수 없다. -> 즉. 함수가 아니면 new를 사용할 수 없다. 

2. 해당 함수의 Prototype Object 생성 및 연결

함수를 정의하면 함수만 생성되는 것이 아니라 Prototype Object도 같이 생성. 생성된 함수는 prototype 속성을 통해 Prototype Object에 접근 가능. 일반적인 객체와 같으며 기본적인 속성으로 constructor와 ``` _proto_```를 가지고 있다.

```javascript
function Person () {} 
// Person.prototype라고 콘솔에 찍어보면
-> consturctor : function Person()
   _proto_ : Object

   여기서 constructor는 Prototype Object와 같이 생성되었던 함수를 지칭.
   _proto_는 Prototype Link
```



```javascript
function Person() {}
    Person.prototype.eyes = 2;
    Person.prototype.nose = 1;
    var kim  = new Person();
    var park = new Person():
	console.log(kim.eyes); // => 2

Person.prototype 접근하면
// Object {eyes : 2, nose 1}
Prototype Object는 일반적인 객체이므로 속성을 마음대로 추가/삭제 할 수 있다. 
kim과 park은 Person 함수를 통해 생성되었으니 Person.prototype을 참조할 수 있다.


```

- Prototype Link  : ```_proto_```

  **prototype** 속성은 함수만 가지지만,
  ```_proto_```속성은 모든 객체가 빠짐없이 가지고 있는 속성.



  ![img](https://cdn-images-1.medium.com/max/800/1*4V9q1tS5GWLU4sMkhOVNEg.png)

  kim객체가 eyes를 직접 가지고 있지 않기 때문에 eyes 속성을 찾을 때까지 상위 프로토타입을 탐색합니다. 최상위인 Object의 Prototype Object까지 도달했는데도 못찾았을 경우 undefined를 리턴합니다. 이렇게 __proto__속성을 통해 상위 프로토타입과 연결되어있는 형태를 프로토타입 체인(Chain)이라고 함.

## 공유와 상속

```javascript
// 공유
var A= function() {};
var B = new A();
A.prototype.x='hello';
console.log(B);
```

![A](http://insanehong.kr/post/javascript-prototype/@img/result1.jpeg)

```javascript
// 상속
var A= function() {this.x='hello';};
var B = new A();
console.log(B);
```

![A](http://insanehong.kr/post/javascript-prototype/@img/result2.jpeg)



## 프로토타입 설명 참조

[속깊은 자바스크립트 강좌] 상속, new와 Object.create의 차이

출처: <http://unikys.tistory.com/320> [All-round programmer]

프로토 타입 이해하기 

> (훌륭한 설명)

https://medium.com/@bluesh55/javascript-prototype-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-f8e67c286b67

좀 어려운 설명 http://insanehong.kr/post/javascript-prototype/





## 상속, NEW와 Object.create

-  Object.create

특정 객체를 프로토 타입으로 하는 객체를 생성해 주는 함수.

