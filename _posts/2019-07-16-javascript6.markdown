---
layout: post
title:  "함수표현방법"
date:   2019-07-16
author: Soob
categories: Survival_JavaScript
---

javascript에서 함수 만드는 방법 3가지
===================================

* 내가 보기에 편한 방법  
function foo(x, y) {  
const result = x + y;  
 return result;  
}

foo(1, 2); //3

* 익명 함수를 변수에 할당 하는 방법  

function(x, y) {  
 return x + y; 
} 
위와 같은 익명 함수를 foo에 할당. 
const foo = function(x, y) {  
 return x + y; 
}

foo(1, 2); //3

* 화살표 함수  
const foo = (x, y) => { 
 return x + y; 
} 
위와 같이 { }내용이 하나의 구문으로 돼있으면, 
const foo = (x, y) => x + y;  
더 축약 할 수 있다.

- 화살표 함수의 다른점
  - 생성자로 사용될 수 없다. 즉, prototype 속성을 가지고 있지 않다.
  - 자기 자신의 this, arguments, super를 가지지 않는다. (함수가 정의된 스코프의 this를 가르킨다.)
  - 내부에서 yield 키워드를 사용 할 수 없다. 즉, 제너레이터로 상용 불가능

이와 같은 특징 때문에 화살표 함수는 함수를 값으로 다루어야 하는 경우(ex. 함수를 다른 함수의 인수로 주는 경우) 사용 된다.

예)  
function AObject(name){  
 this.name;  
 this.getName = () => {return this.name;}  
}

//위의 화살표 함수의 this는 AObject 함수 스코프의 this를 카리킨다.
