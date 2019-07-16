---
layout: post
title:  "rest의 구조분해할당"
date:   2019-07-16
author: Soob
categories: Survival_JavaScript
---

배열 구조분해할당
===================================

function foo1(type, ...rest){
  foo2(rest)
}

function fooe(rest){
  const [a, b] = rest;
}

a, b 에 rest 값들이 차례로 들어간다.
아니 rest도 배열이었나??

아니 rest는 arguments와 달리 Array 인스턴스였다.
rest를 써야겠군..
