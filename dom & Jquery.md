## DOM & jQuery

ELEMENT VS NODE

```
document.getElementById
document.querySelector('#idname');

h2.onclick = function() {
    console.log('click h2');
}
h2.onmouseover
h2.onmouseout

-> interative한 웹사이트를 위해
```



document의 nodelist는 Arraylike (유사 array)며, 

foreach 는 가능.

인덱스로는 접근 가능. 

push 같은 메소드는 적용 안됨.



element 건드리는 자바스크립트 변수의 경우 명명을

var elInput

var elButton 식으로 함.



javascript event list mdn [https://developer.mozilla.org/en-US/docs/Web/Events]



숙제 children node difference Node.childNodes

[`Element.children`](https://developer.mozilla.org/en/DOM/Element.children) returns only element children, while [`Node.childNodes`](https://developer.mozilla.org/En/DOM/Node.childNodes) returns all node children. Note that elements are nodes, so both are available on elements.

I believe `childNodes` is more reliable. For example, MDC (linked above) notes that IE only got `children` right in IE 9. `childNodes` provides less room for error by browser implementors.

```
$('#hello')
.addClass('red')
.on('mouseover',function() {
    $(this).addClass('bold');
})
.on('mouseout', function() {
   $(this).addClass 
});

this는 element 즉, #hello를 가리킴
```



```
console.log( $('#hello').html() );
// 내용을 가져오는 거
$('#hello').html('asdf');
```



```
append/prepend
<div id="result"></div>
var newEl = $('<h4>new element</h4>');

append와 appendTo의 차이는
소스와 타겟이 바뀌어 있음. 그거뿐.

newEl.appendTo('#result');
===
$('#result').append(newEl);
$('#result').prepend(newEl2);


```



## jQuery 알아둬야 할 메소드

- html/text

  $('#hello').html(); hello셀렉터의 내용을 가져옴.

  $('#hello').html('teststs');내용을 채워줌

- append/prepend(뒤에 붙음)

  $(추가 할 요소).appendTo(타겟);

  $(타겟).append(newEL);

  $(타겟).prepend(newEL); 

  주의사항 : appendTo의 경우 문자열에 태그 필요

   $("<p>태그필요</p>").appendTo('.test');

  $("작동안함").appendTo('.test');

- remove / empty

- val

  input 태그에서 가져오는 것

- Event

  - on / off

    jQuery 에서 이벤트 핸들러는 중복 적용이 가능하다.

    


http://htmlcheatsheet.com/jquery/

```
events
basic
selector
DOM Manipulation
정도만 알면 twittler 쉽게 만들 수 있다.
이 내용들은 기억하는게 좋다.

```

jquery.com



- udacity jQuery 

jQuery is simply a Javascript ojbect.

javascript function is also object.



$ = jQuery

$ -> jQuery Collection 

array-alike methods.

$(string)

$(function)

$(Dom Element)

jQuery is just a JavaScript library!

압축된 jQuery 버전을 로딩하는 걸 잊지 말 것. 

$<-jQuery object ('tag')<- selector

$('div'); div 모두 선택.

$('.class') .을 잊어버리지 않을 것.

$('.green') green만 선택.



.parent() 1단계 위

.parents() many 위

.children() 1단계 아래

.find() many 아래

.siblings()



## Selector

```
$("*")                      // all elements
$("p.demo")                 // <p> elements with class="intro"
$("p:first")                // the first <p> element
$("p span")                 // span, descendant of p
$("p > span")               // span, direct child of p
$("p + span")               // span immediately proceeded by a p
$("p ~ span")               // strong element proceeded by p
$("ul li:first")            // the first <li> element of the first <ul>
$("ul li:first-child")      // the first <li> element of every <ul>
$("ul li:nth-child(3)")     // third child
$("[href]")                 // any element with an href attribute
$("a[target='_blank']")     // <a> elements with a target "_blank" attribute
$("a[target!='_blank']")    // <a> elements with a target attribute value other than "_blank"
$(":input")                 // all form elements
$(":button")                // <button> and <input> elements of type="button"
$("tr:even")                // even <tr> elements
$("tr:odd")                 // odd <tr> elements
$("span:parent")            // element which has child element
$("span:contains('demo')")  // element conaining the specified text
Actions  
```

https://zetawiki.com/wiki/JQuery_%EC%85%80%EB%A0%89%ED%84%B0



## 기타 

[[jQuery\] if문으로 요소(element)가 있는지 확인하기.](http://gyuha.tistory.com/343)

```
- ID exists CHECK

javascript way
if ( document.getElementById('myDiv') ) {
    alert('myDiv exists');
}

jQuery way
if ( $('#myDiv').length ) {
    alert('myDiv exists');
}
```

