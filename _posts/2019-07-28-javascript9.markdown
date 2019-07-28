---
layout: post
title:  "비동기를 위한 async await, promise 패턴"
date:   2019-07-28
author: Soob
categories: Survival_JavaScript
---

async await, promise 패턴
=======================

바로 예시 코드를 보며 시작하자.
 
```
async function asyncFunction() {
  try {
    const value = await promise;
  }
  catch (rejectedValue) {
    // …
  }
}
```

함수 정의 앞에 async 키워드를 쓰면 함수 내부에서 await 키워드를 사용 할 수 있다.
await 구문이 있으면, promise가 결정될 때 까지 대기를 한다.
promise가 resolve를 실행하면 값을 리턴받고, 
reject되면 예외를 throw 한다.

참고로, 비동기 함수는 항상 promise를 반환한다. 그래서 promise에 대한 이해도 필요하다는 생각이 든다.
사실 promise를 반환한다는 것 만 알아도 훨씬 쉽게 비동기 함수들을 이해할 수 있다.

그래서, async, await와 promise를 이용해서 delay함수를 만들어 보면
```
function wait(ms) {
  return new Promise(relove => setTimeout(relove, ms));
}

async function usewait() {
  await wait(500);
  return '500ms wait';
}
```
이와 같이 promise 객체를 반환하는 함수를 await 하고, await를 사용하는 함수를 선언 할 때 async 키워드를 써 준다.
