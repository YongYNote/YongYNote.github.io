---
layout: single
title: "스택 & 큐"
description: "이번 포스팅부터 자료구조/알고리즘을 정리해보겠습니다. 첫번째시간은 가장 기초가 되는 스택과 큐입니다."
comments: true
published: true
tags: [Python, Data_Structure]
categories: Data_Structure
classes: wide
typora-copy-images-to: /assets/images/2021-07-19/Stak&Queue
---

###### 이번 포스팅부터 자료구조/알고리즘을 정리해보겠습니다.

첫번째시간은 가장 기초가 되는 스택과 큐입니다.

## 1.스택(Stack)
#### 스택의 개념
스택이란 영어로 Stack 말 그대로 '쌓다'라는 의미입니다.<br>
<center>
<img src="/assets/images/2021-07-19/Stak&Queue/1.png" alt="1"/>
</center>
그림처럼 상단에만 블록을 쌓을수 있다면 가장 마지막에 쌓은 블록을 가정 먼저 뺄 수 있을 것입니다.<br>
이것이 LIFO(Last-In, First-Out)인 스택의 기본 원리가 되겠습니다.<br>

#### 스택의 연산
스택은 LIFO을 따르기에 다음과 같은 연산을 수행할 수 있습니다.<br>
- push(): 데이터 하나를 스택의 가장 윗 부분에 추가
- pop(): 스택에서 가장 위에 있는 항목을 제거
- peek() or top(): 스택의 가장 위에 있는 항목을 반환

#### 스택의 구현
Python을 이용하여 스택을 구현 해볼텐데 Python은 List가 스택으로 사용 가능하도록 이미 너무 잘 구현되어 있기에 간단한 함수 정의로 구현이 가능합니다.<br>


```python
class Stack(list):
    push = list.append

    def peek(self):
        return self[-1]

def main():
    s = Stack()
    s.push(1)
    s.push(5)
    s.push(10)
    print(s) # push 1, 5, 10 의 결과
    print(s.pop()) # pop 호출 시
    print(s) # pop 호출 결과
    print(s.peek()) # peek 호출 시
main()
```

[1, 5, 10]<br>
10<br>
[1, 5]<br>
5<br>
{: .notice--info}

#### 스택의 사용 사례
재귀 알고리즘을 사용하는 경우에 스택에 유용하게 사용 가능합니다.
1. 재귀 알고리즘 
   - 재귀적으로 함수를 호출해야 하는 경우에 임시데이터를 스택에 넣음
   - 재귀함수를 빠져나와 퇴각 검색을 할 때는 스택에 넣어 두었던 임시 데이터를 빼줌
2. 웹 브라우저의 방문기록
   - 웹브라우저 에서 사이트 방문시 기록을 스택에 넣음
   - 이전페이지 확인시 스택에 넣어 두었던 사이트를 빼줌
3. 깊이 우선 탐색(DFS)

## 2.큐(Queue)
#### 큐의 개념
큐는 영어로 Queue '일이 처리되기를 기다리는 리스트'라는 의미입니다.<br>
스택이 한쪽방향에서만 쌓을 수 있었다면 큐는 프로그래밍에서 목록 혹은 리스트에서 접근이 양쪽에서 가능한 구조입니다.<br>
<center>
<img src="/assets/images/2021-07-19/Stak&Queue/2.png" alt="2"/>
</center>
그림처럼 입구와 출구가 나뉘어 있어서 먼저 놓은 블럭이 먼저 나가는 구조가 되며<br>
이것이 FIFO(First-In, First-Out)인 큐의 기본 원리가 되겠습니다.<br>

#### 큐의 연산
큐는 FIFO을 따르기에 다음과 같은 연산을 수행할 수 있습니다.
- put(): 데이터 하나를 큐의 가장 끝 부분에 추가
- get(): 큐에서 첫 번째 항목을 뺌
- peek(): 큐에서 가장 첫번째 있는 항목을 반환

#### 큐의 구현
스택과 마찬 가지로 Python을 이용하여 간단한 함수정의로 구현을 하겠습니다.


```python
class Queue(list):
    put = list.append

    def peek(self):
        return self[0]

    def get(self):
        return self.pop(0)

def main():
    q = Queue()
    q.put(1)
    q.put(5)
    q.put(10)
    print(q) # put 1, 5, 10 의 결과
    print(q.get()) # get 호출 시
    print(q) # get 호출 결과
    print(q.peek()) # pekk 호출 시
main()
```

[1, 5, 10]<br>
1<br>
[5, 10]<br>
5<br>
{: .notice--info}


#### 큐의 사용 사례
데이터가 입력된 시간 순서대로 처리해야 할 필요가 있는 상황에 이용합니다.
1. 선입선출이 필요한 대기열(티켓 카운터)
   - 먼저 입장 가능한 순서 대로 입장
2. 프린트 인쇄 대기열
   - 프린트의 명령을 받은 순서대로 출력
3. 너비 우선 탐색(BFS)
   - 처리해야 할 노드의 리스트를 저장하는 용도로 큐를 사용
