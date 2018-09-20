## checkpoint 4

```javascript
//  5
obj1 = { x : 15}
참조만 함.
obj2.x = 15-> 직접적으로 부여하게 되면 값이 있기 때문에 상위로 올라가지 않으나, 값이 없는 경우엔 상위로 올라가면서 값을 찾음.


// 6
var obj1 = { x: 10 };
var obj2 = Object.create(obj1);
//obj1의 값을 불러올 수 있게 된다
obj2.x += 10;
obj1.x = 15;
// 이 시점에서 obj1  = { x : 15}; obj2 = { x : 20; }
var result = obj2.x;

// 7
자신이 원하는 값을 찾을때까지 상위로 올라감.

// 틀린 문제
8번 - 다음 코드를 실행한 후, result 의 값은 무엇이 될까요?
var obj1 = { x: 10 };
var obj2 = Object.create(obj1);
var obj3 = Object.create(obj2);
obj2.x = 20; // 중간에 값이 들어갔기 때문에 obj1까지 찾아갈 필요가 없음.
var result = obj3.x + 10;
result의 답은?

// 9
사실 Object.create 와 똑같은데, 과정은 똑같은데 new 키워드를 썼을 뿐이다.(더 편함)
함수가 생성되는 순간, 함수의 프로토타입 오브젝트가 메모리 어딘가에 생성이 된다.
(그리고 생성자도 생성이 되지 prototype : constructor : f())

var arr = [];
var arr = new Array() // 이 표현이 위로 줄어든 것 뿐이고, array또 함수로 만들어짐. 다 Array.prototype에서 가져와서 쓰는 것. 만들어진 새 배열에 그떄마다 메소드를 넣어주는게 아니라, 부모의 힘(Array.prototype)을 가져와서 쓰기만 한다.


```

