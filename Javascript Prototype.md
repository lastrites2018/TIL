## Prototype을 이해해보자

## 프로토타입?

[[Construct]]의 기본 전제를 해석해보면, prototype 속성을 사용하는 newTarget은 F를 기본값으로 설정한다고 나와있다. 여기서 F는 new 키워드에서 생성자(constructor)로 호출되는 함수를 의미한다. 이처럼 ECMAScript의 표준 문서에서는 생성자 함수 안에 prototype이라는 속성이 있다고 정의하고 있다. 표준을 살펴보면 생성자를 통해 객체를 생성할 때 생성자의 prototype 속성을 내부적으로 참조하며, 이렇게 생성된 객체들 간의 prototype은 공유된다고 한다. 그리고 이를 상속하는 모든 객체에도 공유된다고 되어 있다. 주목할 점은 생성자의 속성인 prototype 또한 하나의 객체라고 설명하는 부분이다.  



유연함 : **다른 언어와 다르게, 자바스크립트는 생성자를 통해 생성된 객체라도(new Person) 나중에 생성자의 프로토타입에 새로운 속성을 추가할 수 있고, 이렇게 추가된 속성 또한 모든 객체가 공유한다.**

-> c++나 자바의 경우는 헤더나 클래스 몸체가 고정되어 있다! 

수정 가능 : 기존에 선언해 두었던 속성도 다시 수정할 수 있다!



프로토 타입엔 함수가 아닌 변수도 추가 가능 

```javascript
function Person () {};

Person.prototype.gender = 'male';
console.log(unikys.gender); // === male
console.log(stranger.gender); // === male
```

자, 변수를 프로토타입에 추가해서 공유할 수 있으니, prototype의 표준의 정의("prototype은 생성자를 통해 생성된 객체들 간에 공유한다")에 따라 strange 객체의 gender 값을 바꾸면 unikys 객체의 gender값도 바뀔까? 

```javascript
Person.prototype.gender = 'male';
console.log(unikys.gender); // === male
console.log(stranger.gender); // === male

stranger.gender = 'female';
console.log(stranger.gender); // === female
console.log(unikys.gender); // === male 여전히 male이다! 
console.log(Person.prototype.gender) // 이것도 여전히 male이다!
```



> 각 생성자는 prototype이라는 속성을 가지고 있어서, prototype 기반 상속과 속성 공유를 위해 활용된다.



Prototype의 뜻에 대한 여러 버전의 설명 :

1. 자바스크립트의 모든 객체는 자신의 부모 역할을 담당하는 객체와 연결되어 있다. 이것은 마치 객체 지향의 상속 개념과 같이 부모 객체의 프로퍼티 또는 메소드를 상속받아 사용할 수 있게 한다. 이러한 부모 객체를 **Prototype Object(프로토타입 객체)** 또는 줄여서 Prototype(프로토타입)이라 한다.

2. 다른 객체들과 공유되는 속성을 제공하는 객체이다. 생성자가 객체를 생성할 때, 객체는 내부적으로 생성자의 prototype 속성을 활용하여 속성들의 레퍼런스를 참조한다. 생성자의 prototype 속성 constructor.prototype과 같은 표현식으로 프로그램 내에서 접근이 가능하고, 객체의 prototype에 추가된 속성은 상속 받는 객체들까지 함께 공유된다. 또 다른 방법으로는 명시적으로 어떠한 prototype을 사용할지 결정할 수 있는 Object.create 함수를 활용하여 새로운 객체를 생성할 수 있다.



자바에서는 객체를 class로 정의하지만, 자바스크립트에서는 function으로 정의한다.

객체는 언제나 함수 (Function)로 생성된다.



```javascript
function Person () {}  // -> 함수(f부터 }까지의 문자열이 )
var personObject = new Person(); // 함수로 객체 생성
```

personObject는 Person이란 함수로 생성된 객체. 

```javascript
var obj = {}; // 객체 리터럴 방식
// 위 코드와 동일
var obj = new Object();

```

> object도 함수다! Object를 console 창에서 쳐보면 함수로 나옴. 



> 결론적으로 객체 리터럴을 사용하여 객체를 생성한 경우, 그 객체의 프로토타입 객체는 Object.prototype이다.



> 3가지 함수 정의 방식은 결국 Function() 생성자 함수를 통해 함수 객체를 생성한다, 따라서 어떠한 방식으로 함수 객체를 생성하여도 모든 함수 객체의 prototype 객체는 Function.prototype이다. 생성자 함수도 함수 객체이므로 생성자 함수의 prototype 객체는 Function.prototype이다.



## 모든 이들의 부모이자 종점 Object.prototype

- 모든 객체의 부모는 Object.prototype

> 객체 리터럴 방식이나 생성자 함수 방식이나 결국은 모든 객체의 부모 객체인 Object.prototype 객체에서 프로토타입 체인이 끝난다. 이때 Object.prototype 객체를 **프로토타입 체인의 종점(End of prototype chain)**이라 한다.



**함수가 정의될 때는 2가지 일이 동시에 이루어짐**

1. 해당 함수에 Constructor (생성자) 자격 부여

Constructor 자격이 부여되면 new를 통해 객체를 만들어 낼 수 있게 됨. 이것이 함수만이 new 키워드를 사용할 수 있는 이유다. constructor가 아니면 new를 사용할 수 없다. -> 함수가 아니면 new를 사용할 수 없다. 

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



## [[prototype]] ? ```_proto_```? 

ECMAScript spec에서는 **자바스크립트의 모든 객체는 자신의 프로토타입을 가리키는 [[Prototype]]이라는 숨겨진 프로퍼티를 가진다** 라고 되어있다. 크롬, 파이어폭스 등에서는 숨겨진 [[Prototype]] 프로퍼티가 __proto__ 프로퍼티로 구현되어 있다. 즉, __proto__과 [[Prototype]]은 같은 개념이다.

> 주의해야 할 것은 prototype 프로퍼티는 프로토타입 객체를 가리키는 [[Prototype]] 프로퍼티(__proto__ 프로퍼티)와는 다르다는 것이다. prototype 프로퍼티와 [[Prototype]] 프로퍼티는 모두 프로토타입 객체를 가리키지만 관점의 차이가 있다.

```javascript
function Person(name) {
  this.name = name;
}

var foo = new Person('Lee');

console.dir(foo);    // prototype 프로퍼티가 없다.
console.dir(Person); // prototype 프로퍼티가 있다.

```



- [[Prototype]] 프로퍼티

  - 함수를 포함한 모든 객체가 가지고 있다

  - 객체의 입장에선 자신의 부모 프로토타입 객체를 가리키며 함수 객체의 경우 Function.prototype을 가리킨다.

    ```console.log(Person.__proto__ === Function.prototype);```

- prototype 프로퍼티

  - 함수 객체만 가지고 있는 프로퍼티

  - 함수 객체가 생성자로 사용될 때 이 함수를 통해 생성될 객체의 부모 역할을 하는 객체(Prototype Object)를 가리킨다.

    ```console.log(Person.prototype === foo.__proto__);```



## Prototype chain

자바스크립트는 특정 객체의 프로퍼티나 메소드에 접근하려고 할 때 해당 객체에 접근하려는 프로퍼티 또는 메소드가 없다면 [[Prototype]] 프로퍼티가 가리키는 링크를 따라 자신의 부모 역할을 하는 프로토타입 객체의 프로퍼티나 메소드를 차례대로 검색한다. 이것을 프로토타입 체인이라 한다.

```javascript
var student = {
  name: 'Lee',
  score: 90
}

// Object.prototype.hasOwnProperty()
console.log(student.hasOwnProperty('name')); // true
```

student 객체는 hasOwnProperty 메소드를 가지고 있지 않으므로 에러가 발생하여야 하나 정상적으로 결과가 출력되었다. 이는 student 객체의 [[Prototype]] 프로퍼티가 가리키는 링크를 따라가서 student 객체의 부모 역할을 하는 프로토타입 객체(Object.prototype)의 메소드 hasOwnProperty를 호출하였기 때문에 가능한 것이다.

```javascript
var student = {
  name: 'Lee',
  score: 90
}
console.dir(student);
console.log(student.hasOwnProperty('name')); // true
console.log(student.__proto__ === Object.prototype); // true
console.log(Object.prototype.hasOwnProperty('hasOwnProperty')); // true
```



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

https://poiemaweb.com/js-prototype

## 상속, NEW와 Object.create

-  Object.create

특정 객체를 프로토 타입으로 하는 객체를 생성해 주는 함수.

