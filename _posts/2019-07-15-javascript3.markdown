---
layout: post
title:  "콜백함수를 parameter로 줄 때 에러 사례1"
date:   2019-07-15
author: Soob
categories: Survival_JavaScript
---

arr.reduce(callback[, initialValue])
====================================

var maxCallback = function(max, cur){return Math.max(max, cur)}

 - 에러사례 : [ { x: 22 }, { x: 42 } ].reduce( (max, cur) => maxCallback (max, cur));  //typeError -> maxCallback이 function이 아니다.
  - 아마도, maxCallback의 return이 function가 아니기 때문에 발생하는 문제인것 같다.

콜백 함수를 위와 같이 준 이유는, maxCallback에 필요한 parameter를 내가 직접 대입 해 주어야 한다고 생각했다.
 
 
 - 해결 :  [ { x: 22 }, { x: 42 } ].reduce(maxCallback);
  - 함수 자체를 parameter로 준다.
