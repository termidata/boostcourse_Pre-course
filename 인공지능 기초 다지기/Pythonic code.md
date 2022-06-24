## Split

items = 'zero one two'.split()

-> 빈칸을 기준으로 문자열 나누기

items = 'zero,one,two'.split(",")

-> 쉼표를 기준으로 문자열 나누기

---


## join

colors = ['red', 'blue']

result = ''.join(colors) 

-> 리스트 합치기 (redblue)


result = ' '.join(colors)

-> 빈칸 1칸으로 연결 (red blue)

---


## list comprehension 

- 기존 리스트 사용하여 간단히 다른 리스트를 만드는 기법
- for + append 보다 속도가 빠름

result = [i for i in range(10)]

-> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

result = [i for i in range(10) if i % 2 == 0]

-> [0, 2, 4, 6, 8]

(if 조건은 필터라고 함)

```` python

words = 'The quick brown fox jumps over the lazy dog'.split()

stuff = [[w.upper(), w.lower(), len(w) for w in words]]
# 대문자, 소문자, 길이로 변환하여 two dimensional list 변환

````

---

### Two dimensional

result = [[i+j for i in case1] for j in case2]

-> 뒤에가 먼저 작동

---


## enumerate & zip

enumerate = 리스트의 원소를 추출할 때 번호를 붙여서 추출

```` python
for i, v in enumerate(['tic', 'tac', 'toc']):
    print(i, v)

-> 0 tic 
   1 toc ...
````

zip = 두 개의 리스트의 값을 병렬적으로 추출

```` python
alist = [a1, a2, a3]
blist = [b1, b2, b3]
for a, b in zip(alist, blist):
    print(a, b)
-> a1 b1
   a2 b2 ..
````

#### enumerate & zip

```` python
for i, (a,b) in enumerate(zip(alist, blist)):
    print(i, a, b)
-> 0 a1 b1 ..
````

---


## lambda 

- 함수 이름 없이 함수처럼 쓸 수 있는 익명함수

```` python
f = lambda x, y: x+y
print(f(1,4))

(lambda x, y : x + y)(10,50)
````

---


## map

- 두 개 이상의 리스트에도 적용 가능, if 필터에도 가능

```` python
f = lambda x, y: x + y
print(list(map(f, ex, ex)))
````

---


## reduce

- map과 달리 리스트에 똑같은 함수를 적용해서 통합
- 대용량의 데이터를 다룰 때 사용

```` python
from functools import reduce

print(reduce(lambda x,y: x+y, [1,2,3,4,5]))
````

---


## iterable object

- sequence형 자료형에서 데이터를 순서대로 추출

```` python
for city in ['seoul', 'busan', 'pohang']:
    print(city, end='\t')
iter_obj = iter(city)
print(next(iter_obj))
````


## generator

- iterable object를 특수한 형태로 사용해주는 함수
- 원소가 사용되는 시점에 값을 메모리에 반환
- yield를 사용해 한 번에 하나의 원소만 반환

```` python
def generator_list(value):
    result = []
    for i in range(value):
        yield i
````

-> 메모리 주소값만 가지고 있다가, 프린트 할 때만 값을 줌

-> 메모리 주소 절약에 효과

- 리스트 타입의 데이터를 반환해주는 함수는 제너레이터로 만들어라!
- 큰 데이터를 처리할 때는 generator expression을 고려하라!
- 파일 데이터를 처리할 때도 generator를 쓰자!


## function passing arguments

- 함수에 입력되는 arguments의 형태
1. keyword arguments
2. Default arguments
3. variable-length arguments

### keyword arguments

- 함수에 입력되는 parameter의 변수명을 사용, arguments를 넘김

```` python
def print_something(myname, yourname):
    print("Hello {0}, my name is {1}.format(yourname, myname))
````

### Default arguments

- parameter의 기본값을 사용, 입력하지 않을 경우 기본값 출력

```` python
def print_something(myname, yourname='teamlab'):
    print("Hello {0}, my name is {1}.format(yourname, myname))
````

### variable-length asterisk

함수의 parameter가 정해지지 않았다?

다항 방정식? 마트 물건 계산 함수?

#### 가변인자

- 개수가 정해지지 않은 변수를 함수의 parameter로 사용하는 법
- asterisk(*) 기호를 사용하여 함수의 parameter 표시
- 오직 한 개만 맨 마지막 위치에 사용 가능
- 일반적으로 *args를 변수명으로 사용
- 기존 parameter 이후에 나오는 값을 tuple로 지정

```` python
def asterisk_test(a, b, *args):
    return a+b+sum(args)
print(asterisk_test(1,2,3,4,5))

-> 3,4,5가 args에 튜플 타입으로 들어감
````

#### 키워드 가변인자

- parameter 이름을 따로 지정하지 않고 입력하는 방법
- asterisk(*) 두개를 사용하여 함수의 parameter 표시
- 입력된 값은 dict type으로 사용할 수 있음

```` python
def test(**kwargs):
    print(kwargs)

def test2(**kwargs):
    print("first value is {first}".format(**kwargs))
````

#### asterisk - unpacking a container

- tuple, dict 등 자료형에 들어가 있는 값을 unpacking
- 함수의 입력값, zip 등에 유용하게 사용

```` python
ex = ([1,2],[3,4],[5,6])
for value in zip(*ex):
    print(value)
-> (1,3,5)
   (2,4,6)
````