---
layout: post
title:  "비동기 프로그래밍(Promise 와 generator function 패턴)"
date:   2019-07-22
author: Soob
categories: Survival_JavaScript
---

generator function
==================================
Generator 함수는 호출되어도 즉시 실행되지 않고, 대신 함수를 위한 Iterator 객체가 반환된다.

반환된 Iterator의 next() 함수를 호출해 yield문을 만날때 까지 진행.

이후 다시 next()함수를 호출하면 멈췄던 위치에서 재실행.

next()를 호출했을 때 반환되는 값은 value 와 done(boolean type)을 갖는다.

next()에 파라미터를 주고 호출 할 경우, yield문을 호출 할 때 준 파라미터로 치환한다.


Promise
==================================

Promise 객체가 반환되면 , Promise객체의 콜백함수의 파라미터가 resolve를 가지고 있으면, then 문이 실행
reject를 가지고 있으면, catch 문이 실행된다.
