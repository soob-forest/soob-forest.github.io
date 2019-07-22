---
layout: post
title:  "bind(this)"
date:   2019-07-22
author: Soob
categories: Survival_JavaScript
---

func.bind(thisArg)
=================

함수와 객체를 묶어준다.

 - 객체로부터 메소드를 추출한 뒤 나중에 그 함수의 원 객체를 그 함수의 this로서 사용하기를 기대 할 때, 보통 원 객체는 손실된다.(콜백 함수 내부)
 
 this.x = 9;
var module = {
  x: 81,
  getX: function() { return this.x; }
};

module.getX(); // 81

var retrieveX = module.getX;

retrieveX(); //9 반환

var boundgetX = retrievX.bind(module);

boundgetX();  //81 반환


 - setTime과 함께 사용
 
```
class A{

  setTimeout( function (){
  
  this.Afunc()  // 여기서 this는 Time out
      
  })
  
}

class A{

  setTimeout( function (){
  
      this.Afunc()  // 여기서 this는 A
      
  }.bind(this))
  
}
```
