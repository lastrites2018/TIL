# 지금 말고 나중에야 도전해볼 것들

지금은 너무 어렵거나, 아직 때가 아니다.



- javascript

Array prototype 사용하기 https://www.bsidesoft.com/?p=323

자바스크립트 클래스 개념 https://www.bsidesoft.com/?p=320

재귀호출문을 반복으로 바꾸기 https://www.bsidesoft.com/?p=4314

뉴비를 위한 mv 패턴 3 https://www.bsidesoft.com/?p=5964 

Array.prototype.slice.call ()은 어떻게 작동합니까? https://code.i-harness.com/ko/q/6bae1d

[jsdp] 객체지향 자바스크립트와 디자인패턴 #1 https://www.bsidesoft.com/?p=877

연산지연 https://www.bsidesoft.com/?p=773#%25ea%25b2%25b0%25eb%25a1%25a0



```javascript
var a = 0;
 
//문
if( !a ) a = 'ok';
 
//식
a || a = 'ok';
이런 연산지연은 조건분기연산자로 대체할 수도 있습니다.

var a = 0;
 
a ? a = 'ok' : null;
거짓일 때의 처리가 없으므로 그냥 null 을 넣어주면 그만입니다. 
언틋보면 && 와 || 이 짧고 더 좋아보입니다.
하지만 연산지연은 조건분기연산자보다 느리고 심지어 if 문보다도 느립니다. 조건분기연산자나 if문은 처음부터 분기된 뒤에 실행할 식 또는 문의 적재공간을 확보하도록 구현되어있는데 비해 &&나 ||은 차례대로 진행되며 실행되거나 멈추는 처리를 하기 때문에 효율적이지 않게 됩니다. 따라서 단순한 할당에는 쓸만합니다만 본격적인 조건분기에는 사용하지 않는 편이 유리합니다.
주로 사용되는 곳은 함수의 기본값 할당 입니다.

function command(){
  var order;
  order = arguments[0] || 'action1';
  ...
}
 
command(); //order == action1
위의 예에서 인자를 받은 경우는 order에 할당하지만 없는 경우는 action1이 됩니다. 하지만 0, ”, null 등으로 넘어와도 action1이 되므로 취약한 구조입니다. 제이쿼리 등 수 많은 라이브러리에서 자주 보이는 코드지만 실제 안정성에는 문제가 많아지기 때문에 적어도 조건분기연산자 정도가 적당하겠죠.

function command(){
  var order;
  order = arguments[0] === 'undefined' ? 'action1' : arguments[0];
}
이렇듯 연산지연시스템의 다양한 면을 둘러봤습니다만 정작 무엇이 스택시스템과 다른지 설명하지 않았습니다.
연산지연은 한단계씩 진행하면서 다음 단계로 넘어가거나 혹은 그 단계의 값을 반환하기 때문에 스택공간이 필요없습니다. 따라서 단계별로 매번 식을 진행할지 말지를 판단하는 요소가 개입되어 느리지만 스택오버플로우의 위험성이 없습니다.

```



- 소수찾기

https://phillyai.github.io/2018-05-02-Find-Primes/

https://code.i-harness.com/ko/q/b69838



# swift

https://outofbedlam.github.io/swift/2016/02/12/functional-programming/

 함수형 프로그래밍과 배열의 filter, reduce, map