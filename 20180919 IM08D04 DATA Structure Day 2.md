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





