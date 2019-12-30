---
layout: post
title:  "그래프 자료구조 및 dfs 구현"
date:   2019-12-30
author: Soob
categories: Survival_Algorithm
---

## 첫 번째, 자료구조, 알고리즘

### 또 다시 생존을 위한 혈투가 시작된다.


# 그래프

그래프가 어떤 것인지 모르는 사람은 없을거라 생각된다.

띄웅?? 모르면 구글링 하시면 됩니다.

이번 장의 목표는 자바스크립트 스러운 자료구조를 만드는 것이 목표다.

사실 그냥 prototype을 통해 자료구조를 만들어 보고 싶은 마음에 해 보았다.

그래프는 Vertex만 가지고 있으면 된다고 생각했고, Vertex라는 자료구조를 이용해 그래프의 Edge를 표현할 수 있다 생각했다.

그리고 구현하기에 인접행렬을 이용하는 것 보다, 링크드 리스트를 이용하는게 더 쉽게 느껴져, 

그래프의 Vertex는 링크드 리스트를 이용해 구현했다.

그래서 구현물은??!

```
const myGraph = function () {
    this.vertexs = [];
}

const Vertex = function (data, index, next) {
    this.data = data;
    this.index = index;
    this.next = next;
}

myGraph.prototype.addVertex = function (index, data) {
    const vertex = new Vertex(data, index)
    this.vertexs[index] = vertex;
}

myGraph.prototype.addEdge = function (startData, endData) {
    const startVertex = this.vertexs.filter(vertex => vertex.data === startData);
    let tempVertex = startVertex[0];
    while (tempVertex.next) {
        tempVertex = tempVertex.next;
    }
    const vertex = new Vertex(endData)
    tempVertex.next = vertex;
}

myGraph.prototype.printGraph = function () {
    console.log('======print Graph======')
    this.vertexs.forEach((vertex) => {
        let tempVertex = vertex;
        let string = ''
        while (tempVertex) {
            string = string + '->' + tempVertex.data;
            tempVertex = tempVertex.next;
        }
        console.log(string.slice(2))
    })
}


myGraph.prototype.dfs = function (startData, endData) {
    console.log('======dfs Start======')
    const stack = [];
    const visiteds = new Array(this.vertexs.length);
    visiteds.forEach((visited) => {
        visited = false;
    })

    const startVertex = this.vertexs.filter(vertex => vertex.data === startData)[0];
    stack.push(startVertex);
    while (stack) {
        const vertex = stack.pop();
        console.log(vertex.data);
        console.log('↓');
        if (vertex.data === endData) break;

        let tempVertex = vertex.next;
        while (tempVertex) {
            const adjenctVertex = this.vertexs.filter(vertex => vertex.data === tempVertex.data)[0];
            if (!visiteds[adjenctVertex.index]) {
                stack.push(adjenctVertex);
                visiteds[adjenctVertex.index] = true;
            }
            tempVertex = tempVertex.next;
        }
    }
    console.log('end')
}

const graph = new myGraph();

graph.addVertex(0, 'A');
graph.addVertex(1, 'B');
graph.addVertex(2, 'C');
graph.addVertex(3, 'D');

graph.addEdge('A', 'B')
graph.addEdge('B', 'C')
graph.addEdge('B', 'D')
graph.addEdge('C', 'D')


graph.printGraph();

graph.dfs('A', 'D');
```

짠.

