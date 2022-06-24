## 스택

- 나중에 넣은 데이터를 먼저 반환
- Last In First Out (LIFO)
- 입력을 Push, 출력을 Pop

```` Python

a = [1,2,3,4,5]
a.append(10)
a.append(20)
a.pop() 
# 20 출력

# pop() 함수는 return을 하면서 변환시키는 특이한 함수

````

___

## 큐

- 먼저 넣은 데이터를 먼저 반환하도록 설계된 메모리 구조
- First in First Out (FIFO)

```` Python

a = [1,2,3,4,5]
a.append(10)
a.append(20)
a.pop(0) 
# 1 출력

````

___

## 튜플

- **값 변경이 불가능한 리스트**
- 선언 시 []가 아닌 ()를 사용
- 리스트의 연산, 인덱싱, 슬라이싱 등을 동일하게 사용

왜 쓸까?
- 프로그램을 작동하는 동안 변경되지 않은 데이터의 저장
- 함수의 변환 값등 사용자의 실수에 의한 에러를 사전에 방지

___

## 집합(set)

- 값을 순서없이 저장, 중복 불허 하는 자료형
- set 객체 선언을 이용하여 객체 생성
- 수학에서 활용하는 다양한 집합 연산 가능

___

## 사전(dict)

- 데이터를 저장할 때는 구분 지을 수 있는 값을 함께 저장
- 구분을 위한 데이터 고유 값을 Idenrifier or Key 라고함
- key 값을 활용하여, 데이터 값(value)를 관리
- key와 value를 매칭하여 key로 value를 검색
- {key1:value1, key2:value2, ...}

code.items() -> 데이터 쌍 출력
code.keys() -> 키 값만 출력
code.values() -> value만 출력

___

## collections

- List, Tuple, Dict에 대한 Python Built-in 확장 자료 구조(모듈)
- 편의성, 실행 효율 등을 사용자에게 제공


### deque

- Stack, Queue를 지원하는 모듈
- 리스트에 비해 효율적인 = 빠른 자료 저장 방식을 지원

```` python

from collections import deque

deque_list = deque()
for i in range(5):
    deque_list.append(i)

````

- rotate, reverse 등 Linked List의 특성을 지원
- 기존 리스트 형태의 함수를 모두 지원


### orderedDict

- dict와 달리, 데이터를 입력한 순서대로 dict를 반환
- 지금은 dict도 가능함!


### defaultdict

- dict의 type의 값에 기본값을 지정, 신규값 생성시 사용하는 방법

```` python

from collections import defaultdict

d = defaultdict(object)
d = defaultdict(lambda: 0) # default 값을 0으로 설정
print(d["first"])

````

- 하나의 지문에 각 단어들이 몇 개나 있는지 세고 싶은 경우 사용


### Counter

- Sequence type의 data element들의 갯수를 dict 형태로 반환 

```` python

from collections import Counter

c = Counter()
c = Counter('gallahad')
print(c)
# 각 알파벳마다 몇 개 있는지 세줌

````


### namedtuple

- tuple 형태로 data 구조체를 저장하는 방법
- 저장되는 데이터의 variable을 사전에 지정해서 저장

```` python

from collections import namedtuple

Point = namedtuple('Point', ['x', 'y'])
p = Point(11, 22)

````
