# Python_Study



#### 1. List

[ ] 으로 나타냄, 갱신가능, mutable

```python
x=[1,2,3,4]
xx = ["hello", "there"]
num_elements = len(x)	# 4

y = sorted(x)
print(y)

z = sum(x)
print(z)

for n in x:
    print(n)	#list안에 있는 element를 차례대로 다 출력

print(x.index(3))	#3이란 숫자의 index를 알려준다. 2
print(xx.index("hello"))	#hello란거의 index를 알려준다. 0

print("hello" in xx)	#hello가 xx에 있는가? -> True

```



#### 2. Tuple

( ) 으로 나타냄, 갱신 불가능, immutable

```python
x = (1,2,3)
y = ('a', 'b', 'c')
z = (1, "hello", "there")

print(x+y)
print('a' in y)
print(z.index("hello"))

x[0] = 10 	#이거는 안됨. 불가변하기때문에
```



#### 3. Dictionary

{ } 으로 나타냄, x = { key1 : , key 2:, . . . } , 여기서 key에 list는 가변이라서 못씀, 갱신이 가능하여 바꾸거나 새로운거 집어넣을수 있음.

x.keys() 와 x.values() 요런식으로 가능

```python
x = dict()
y = {}
# 이렇게 두가지 방식으로 만들 수 있음

x = {
    0: "hello",
    1: "Bye",
    "name" : "근수",
    "age" : 27,	#마지막에 반점 꼭 찍어야함
}

print(x["name"]) 	# 근수출력
print(x[0])	# hello 출력됨

print("age" in x)	# True 출력

print(x.keys())		# 모든 key 값 출력
print(x.values())	# 모든 values 값 출력

for key in x:
    print(key)		#dict인 x의 모든 key값 탐색하면서 출력
    print(x[key])	#dict인 x의 모든 values값 탐색하면서 출력
    
    
x[0] = "Fuck you"	#여기서 "hello"를 "Fuck you"로 변경 가능
x["school"] = "경북대"	#여기서는 이러한 key값과 value를 추가로 생성 가능
```





#### 반복문 

while 중에 continue사용 가능, 바로 위로 올라감

if, elif, else

if ~~~ :

else ~~~~~ :





##### 여러라인 출력하려면 

```python
z = """
안녕
이렇게
여러 줄로
하려면 큰따움표 세번
"""
```





#### Class

```python
class Person:
  def __init__(self, name):# 여기서 name은 받을 인자임 여기서 더받으려면 쭉쭊가능
    self.name = name

  def say_hello(self, to_name):	# say_hello에 받을 인자를 self다음으로 쭉쭉
    print("Hi " + to_name +" my name is " + self.name)

justin = Person("justin")

justin.say_hello("Tom")


class Police(Person): #Police란 class가 Person이라는 clamss를 상속함
  def arrest(self, to_arrest):
    print("under arrested, " + to_arrest)
    

justin = Person("justin")
jenny = Police("Jenny")#Jenny는 Person과 Police의 함수들을 다 공짜로 사용가능
jenny.arrest("justin")#요렇게 사용가능
```



#### Package

package안에 module들을 만들어보자



animal이라는 Package안에 3개의 파일이 있음

dog.py

```python
class DogClass:
    def hi(self):
        print("bark!")
```



cat.py

```python
class CatClass:
    def hi(self):
        print("meow")
```



_init__.py

```python
from .cat import CatClass 	# .을 찍은거는 이 폴더에 있는 이라는 의미이고 cat이라는 파일에서 Cat이라는 클래스를 갖고와줘
from .dog import DogClass	# 동일함
```



밖에 main.py

```python
from animal.dog import DogClass	# animal 패키지에서 dog라는 모듈을 갖고와줘
from animal.cat import CatClass	# animal 패키지에서 cat라는 모듈을 갖고와줘

d = dog.DogClass()
d.hi()

c = cat.CatClass()
c.hi()

from animal import * 	# animal 패키지가 갖고 있는 모듈을 다 갖고와
d = DogClass()
c = CatClass()

d.hi()
c.hi()
```



이런식으로 다른 패키지를 가져올 수 있음



## List에서의 append vs extend

list.append(x) : 리스트 끝에 x 한개를 넣음

list.extend(itrable) : 리스트 끝에 iterable의 모든 항목을 넣음



1. append

```python
x = ['A', 'B', 'C']
y = ['D', 'E']
x.append(y)
print ('x : ', x)
# x : ['A', 'B', 'C', ['D', 'E']]
```



2. extend

```python
x = ['A', 'B', 'C']
y = ['D', 'E']
x.extend(y)
print ('x : ', x)
# x : ['A', 'B', 'C', 'D', 'E']
```





## List의 2차원 배열 만들고, 모든 원소 뽑기



2차원 배열 만들기

```python
# 동적
array = [[0 for row in range(11)] for col in range(10)]
#  row : 행 = 가로줄, col : 열 = 세로줄

# 정적
array = [[0] * 11] * 10
```



2차원 배열 원소 모두 뽑기

```python
for element in array: #만약 array의 열이 3이면
    i, j, k = element[0], element[1], element[2] #이것도 가능하고
	i, j, k = element # 이것도 가능함
```



import numpy

```python
import numpy
numpy.zeros((5,5))

#5*5배열의 0으로 된 2차원 배열 생성
```



## Slice 함수

```python
array = []
slice = array[i-1:j]	#i번째부터 j번째까지 잘라옴
```



## enumerate 함수

리스트가 있는 경우, 순서와 리스트의 값을 전달하는 기능을 가짐.

이 함수는 순서가 있는 자료형 (list, set, tuple, dictionary, string)을 입력으로 받아 인덱스 값을 포함하는 enumerate 객체를 리턴함.

for문과 함께 사용됨

```python
for i, name in enumerate(['body', 'foo', 'bar']):
    print(i, name)
    
#	0 body 1 foo 2 bar
```



## abs 함수

abs(x)는 절댓값 x를 돌려주는 함수

```python
>>>abs(3)
3
>>>abs(-3)
3
>>>abs(-1.2)
1.2
```



## all

all(x)는 반복 가능한(iterable) 자료형 x를 입력 인수로 받으며 이 x의 요소가 모두 참이면 True, 거짓이 하나라도 있으면 False를 돌려준다.

> ※ 반복 가능한 자료형이란 for문으로 그 값을 출력할 수 있는 것을 의미한다. 리스트, 튜플, 문자열, 딕셔너리, 집합 등이 있다.

다음 예를 보자.

```python
>>> all([1, 2, 3])
True
```

리스트 자료형 [1, 2, 3]은 모든 요소가 참이므로 True를 돌려준다.

```python
>>> all([1, 2, 3, 0])
False
```

리스트 자료형 [1, 2, 3, 0] 중에서 요소 0은 거짓이므로 False를 돌려준다.

```python
>>> all([])
True
```

만약 all의 입력 인수가 빈 값인 경우에는 True를 리턴한다. (주의)



## any

any(x)는 반복 가능한(iterable) 자료형 x를 입력 인수로 받으며 이 x의 요소 중 하나라도 참이 있으면 True를 돌려주고, x가 모두 거짓일 때에만 False를 돌려준다. all(x)의 반대이다.

다음 예를 보자.

```python
>>> any([1, 2, 3, 0])
True
```

리스트 자료형 [1, 2, 3, 0] 중에서 1, 2, 3이 참이므로 True를 돌려준다.

```python
>>> any([0, ""])
False
```

리스트 자료형 [0, ""]의 요소 0과 ""은 모두 거짓이므로 False를 돌려준다.

```python
>>> any([])
False
```

만약 any의 입력 인수가 빈 값인 경우에는 False를 리턴한다.



## chr

chr(i)는 아스키(ASCII) 코드 값을 입력받아 그 코드에 해당하는 문자를 출력하는 함수이다.

```python
>>> chr(97)
'a'
>>> chr(48)
'0'
```





## divmod

divmod(a, b)는 2개의 숫자를 입력으로 받는다. 그리고 a를 b로 나눈 몫과 나머지를 Tuple 형태로 돌려주는 함수이다.

```python
>>> divmod(7, 3)
(2, 1)
```

몫을 구하는 연산자 `//`와 나머지를 구하는 연산자 `%`를 각각 사용한 결과와 비교해 보자.

```python
>>> 7 // 3
2
>>> 7 % 3
1
```



## eval

eval(expression )은 실행 가능한 문자열(1+2, 'hi' + 'a' 같은 것)을 입력으로 받아 문자열을 실행한 결괏값을 돌려주는 함수이다.

```python
>>> eval('1+2')
3
>>> eval("'hi' + 'a'")
'hia'
>>> eval('divmod(4, 3)')
(1, 1)
```

보통 eval은 입력받은 문자열로 파이썬 함수나 클래스를 동적으로 실행하고 싶을 때 사용한다.



## filter

filter 함수는 첫 번째 인수로 함수 이름을, 두 번째 인수로 그 함수에 차례로 들어갈 반복 가능한 자료형을 받는다. 그리고 두 번째 인수인 반복 가능한 자료형 요소가 첫 번째 인수인 함수에 입력되었을 때 반환 값이 참인 것만 묶어서(걸러 내서) 돌려준다.

다음 예를 보자.

```python
#positive.py 
def positive(l): 
    result = [] 
    for i in l: 
        if i > 0: 
            result.append(i) 
    return result

print(positive([1,-3,2,0,-5,6]))
```

> 결과값: [1, 2, 6]

즉 위에서 만든 positive 함수는 리스트를 입력값으로 받아 각각의 요소를 판별해서 양수 값만 돌려주는 함수이다.

filter 함수를 사용하면 위 내용을 다음과 같이 간단하게 작성할 수 있다.

```python
#filter1.py
def positive(x):
    return x > 0	#와 이렇게 함수 return값에 0보다 크다라고 지정해두면 filter 함수를 쓰면 두줄만에 정리가 되는구나!

print(list(filter(positive, [1, -3, 2, 0, -5, 6])))
```

> 결과값: [1, 2, 6]

여기에서는 두 번째 인수인 리스트의 요소들이 첫 번째 인수인 positive 함수에 입력되었을때 반환 값이 참인 것만 묶어서 돌려준다. 앞의 예에서는 1, 2, 6만 양수여서 x > 0 문장이 참이되므로 [1, 2, 6]이라는 결괏값을 돌려주게 된 것이다.



앞의 함수는 lambda를 사용하면 더욱 간편하게 코드를 작성할 수 있다.

```python
>>> list(filter(lambda x: x > 0, [1, -3, 2, 0, -5, 6]))		#labda 함수는 return값을 더욱 간단하게 바로 지정할 수 있구나!
[1, 2, 6]
```



## hex

hex(x)는 정수 값을 입력받아 16진수(hexadecimal)로 변환하여 돌려주는 함수이다.

```python
>>> hex(234)
'0xea'
>>> hex(3)
'0x3'
```



## id

id(object)는 객체를 입력받아 객체의 고유 주소 값(레퍼런스)을 돌려주는 함수이다.

```python
>>> a = 3
>>> id(3)
135072304
>>> id(a)
135072304
>>> b = a
>>> id(b)
135072304
```

위 예의 3, a, b는 고유 주소 값이 모두 135072304이다. 즉 3, a, b가 모두 같은 객체를 가리키고 있다.

만약 id(4)라고 입력하면 4는 3, a, b와 다른 객체이므로 당연히 다른 고유 주소 값이 출력된다.

```python
>>> id(4)
135072292
```



## isinstance

isinstance(object, class )는 첫 번째 인수로 인스턴스, 두 번째 인수로 클래스 이름을 받는다. 입력으로 받은 인스턴스가 그 클래스의 인스턴스인지를 판단하여 참이면 True, 거짓이면 False를 돌려준다.

```python
>>> class Person: pass
...
>>> a = Person()
>>> isinstance(a, Person)
True
```

위 예는 a가 Person 클래스가 만든 인스턴스임을 확인시켜 준다.

```python
>>> b = 3
>>> isinstance(b, Person)
False
```

b는 Person 클래스가 만든 인스턴스가 아니므로 False를 돌려준다.



## len

len(s)은 입력값 s의 길이(요소의 전체 개수)를 돌려주는 함수이다.

```python
>>> len("python")
6
>>> len([1,2,3])
3
>>> len((1, 'a'))
2
```



## list

list(s)는 반복 가능한 자료형 s를 입력받아 리스트로 만들어 돌려주는 함수이다.

```python
>>> list("python")
['p', 'y', 't', 'h', 'o', 'n'] 		#오 이렇게도 되는군
>>> list((1,2,3))
[1, 2, 3]
```

list 함수에 리스트를 입력으로 주면 똑같은 리스트를 복사하여 돌려준다.

```python
>>> a = [1, 2, 3]
>>> b = list(a)		# 오 이렇게 하면 리스트를 복사할수 도 있겠군
>>> b
[1, 2, 3]
```



## map

**map(f, iterable)**은 **함수(f)**와 **반복 가능한(iterable) 자료형**을 입력으로 받는다. map은 입력받은 자료형의 각 요소를 함수 f가 수행한 결과를 묶어서 돌려주는 함수이다. 

map함수쓸때 첫번째 인자 join으로 하면 문자열로 반환합니다! 

다음 예를 보자.

```python
# two_times.py
def two_times(numberList):
    result = [ ]
    for number in numberList:
        result.append(number*2)
    return result

result = two_times([1, 2, 3, 4])
print(result)
```

two_times 함수는 리스트 요소를 입력받아 각 요소에 2를 곱한 결괏값을 돌려준다. 실행 결과는 다음과 같다.

> 결과값: [2, 4, 6, 8]



위 예제는 map 함수를 사용하면 다음처럼 바꿀 수 있다.

```python
>>> def two_times(x): 
...     return x*2
...
>>> list(map(two_times, [1, 2, 3, 4]))
[2, 4, 6, 8]
```

이제 앞 예제를 해석해 보자. 먼저 리스트의 첫 번째 요소인 1이 two_times 함수의 입력값으로 들어가고 `1 * 2`의 과정을 거쳐서 2가 된다. 다음으로 리스트의 두 번째 요소인 2가 `2 * 2` 의 과정을 거쳐 4가 된다. 따라서 결괏값 리스트는 이제 [2, 4]가 된다. 총 4개의 요솟값이 모두 수행되면 마지막으로 [2, 4, 6, 8]을 돌려준다. 이것이 map 함수가 하는 일이다.

> ※ 위 예에서 map의 결과를 리스트로 보여 주기위해 list 함수를 사용하여 출력하였다.

앞의 예는 lambda를 사용하면 다음처럼 간략하게 만들 수 있다.

```python
>>> list(map(lambda a: a*2, [1, 2, 3, 4]))
[2, 4, 6, 8]
```



## max

max(iterable)는 인수로 반복 가능한 자료형을 입력받아 그 최댓값을 돌려주는 함수이다.

```python
>>> max([1, 2, 3])
3
>>> max("python")
'y'
```



## min

min(iterable)은 max 함수와 반대로, 인수로 반복 가능한 자료형을 입력받아 그 최솟값을 돌려주는 함수이다.

```python
>>> min([1, 2, 3])
1
>>> min("python")
'h'
```



## oct

oct(x)는 정수 형태의 숫자를 8진수 문자열로 바꾸어 돌려주는 함수이다.

```python
>>> oct(34)
'0o42'
>>> oct(12345)
'0o30071'
```



## open

open(filename, [mode])은 "파일 이름"과 "읽기 방법"을 입력받아 파일 객체를 돌려주는 함수이다. 읽기 방법(mode)을 생략하면 기본값인 읽기 전용 모드(r)로 파일 객체를 만들어 돌려준다.

| mode | 설명                      |
| :--- | :------------------------ |
| w    | 쓰기 모드로 파일 열기     |
| r    | 읽기 모드로 파일 열기     |
| a    | 추가 모드로 파일 열기     |
| b    | 바이너리 모드로 파일 열기 |

b는 w, r, a와 함께 사용한다.

```python
>>> f = open("binary_file", "rb")
```

위 예의 rb는 "바이너리 읽기 모드"를 의미한다.

다음 예의 fread와 fread2는 동일한 방법이다.

```python
>>> fread = open("read_mode.txt", 'r')
>>> fread2 = open("read_mode.txt")
```

즉 모드 부분을 생략하면 기본값으로 읽기 모드 r를 갖게 된다.

다음은 추가 모드(a)로 파일을 여는 예이다.

```python
>>> fappend = open("append_mode.txt", 'a')
```



## ord

ord(c)는 문자의 아스키 코드 값을 돌려주는 함수이다.

> ※ ord 함수는 chr 함수와 반대이다.

```python
>>> ord('a')
97
>>> ord('0')
48
```



## pow

pow(x, y)는 x의 y 제곱한 결괏값을 돌려주는 함수이다.

```python
>>> pow(2, 4)
16
>>> pow(3, 3)
27
```



## range

range([start,] stop [,step] )는 for문과 함께 자주 사용하는 함수이다. 이 함수는 입력받은 숫자에 해당하는 범위 값을 반복 가능한 객체로 만들어 돌려준다.



**인수가 하나일 경우**

시작 숫자를 지정해 주지 않으면 range 함수는 0부터 시작한다.

```python
>>> list(range(5))
[0, 1, 2, 3, 4]
```



**인수가 2개일 경우**

입력으로 주어지는 2개의 인수는 시작 숫자와 끝 숫자를 나타낸다. 단 끝 숫자는 해당 범위에 포함되지 않는다는 것에 주의하자.

```python
>>> list(range(5, 10))
[5, 6, 7, 8, 9]
```



**인수가 3개일 경우**

세 번째 인수는 숫자 사이의 거리를 말한다.

```python
>>> list(range(1, 10, 2)) # 오 이렇게 1부터 10까지 2만큼의 간격의 list로도 출력할수 있구만
[1, 3, 5, 7, 9]

>>> list(range(0, -10, -1))
[0, -1, -2, -3, -4, -5, -6, -7, -8, -9]
```



## round

round(number[, ndigits]) 함수는 숫자를 입력받아 반올림해 주는 함수이다.

> ※ [, ndigits]는 ndigits가 있을 수도 있고 없을 수도 있다는 의미이다.

```python
>>> round(4.6)
5
>>> round(4.2)
4
```



다음과 같이 실수 5.678을 소수점 2자리까지만 반올림하여 표시할 수 있다.

```python
>>> round(5.678, 2)
5.68
```



round 함수의 두 번째 매개변수는 반올림하여 표시하고 싶은 소수점의 자릿수(ndigits)이다.



## sorted

sorted(iterable) 함수는 입력값을 정렬한 후 그 결과를 리스트로 돌려주는 함수이다.

```python
>>> sorted([3, 1, 2])
[1, 2, 3]
>>> sorted(['a', 'c', 'b'])
['a', 'b', 'c']
>>> sorted("zero")
['e', 'o', 'r', 'z']
>>> sorted((3, 2, 1))
[1, 2, 3]
```

리스트 자료형에도 sort 함수가 있다. 하지만 리스트 자료형의 sort 함수는 리스트 객체 그 자체를 정렬만 할 뿐 정렬된 결과를 돌려주지는 않는다.

**주의** : 리스트 자료형에 있는 **sort 함수** vs **sorted 함수** 



## str

str(object)은 문자열 형태로 객체를 변환하여 돌려주는 함수이다.

```python
>>> str(3)
'3'
>>> str('hi')
'hi'
>>> str('hi'.upper())
'HI'
```



## sum

sum(iterable) 은 입력받은 리스트나 튜플의 모든 요소의 합을 돌려주는 함수이다.

```python
>>> sum([1,2,3])
6
>>> sum((4,5,6))
15
```



## tuple

tuple(iterable)은 반복 가능한 자료형을 입력받아 튜플 형태로 바꾸어 돌려주는 함수이다. 만약 튜플이 입력으로 들어오면 그대로 돌려준다.

```python
>>> tuple("abc")
('a', 'b', 'c')
>>> tuple([1, 2, 3])
(1, 2, 3)
>>> tuple((1, 2, 3))
(1, 2, 3)
```



## type

type(object)은 입력값의 자료형이 무엇인지 알려 주는 함수이다.

```python
>>> type("abc")
<class 'str'>
>>> type([ ])
<class 'list'>
>>> type(open("test", 'w'))
<class '_io.TextIOWrapper'>
```



## zip

`zip(*iterable)`은 동일한 개수로 이루어진 자료형을 묶어 주는 역할을 하는 함수이다.

> ※ 여기서 사용한 `*iterable`은 반복 가능(iterable)한 자료형 여러 개를 입력할 수 있다는 의미이다.



잘 이해되지 않는다면 다음 예제를 살펴보자.

```python
>>> list(zip([1, 2, 3], [4, 5, 6]))
[(1, 4), (2, 5), (3, 6)]
>>> list(zip([1, 2, 3], [4, 5, 6], [7, 8, 9]))
[(1, 4, 7), (2, 5, 8), (3, 6, 9)]
>>> list(zip("abc", "def"))
[('a', 'd'), ('b', 'e'), ('c', 'f')]
```



## 순열과 조합

permutations 와 combinations는 list로 반환해야함

list로 반환해서 print하면 [(1,2), (3,4), . . . ] 요런식으로 됨

그래서 map함수를 해서 print로 반환

1. 순열

```python
from itertools import permutations

items = ['A', 'B', 'C', 'D'] 
print(list(map(''.join, permutations(items)))) # items의 모든 원소를 가지고 순열을 만든다.
print(list(map(''.join, permutations(items, 2)))) # 2개의 원소를 가지고 순열을 만든다

>>['ABCD', 'ABDC', 'ACBD', 'ACDB', 'ADBC', 'ADCB', 'BACD', 'BADC', 'BCAD', 'BCDA', 'BDAC', 'BDCA', 'CABD', 'CADB', 'CBAD', 'CBDA', 'CDAB', 'CDBA', 'DABC', 'DACB', 'DBAC', 'DBCA', 'DCAB', 'DCBA']

>> ['AB', 'AC', 'AD', 'BA', 'BC', 'BD', 'CA', 'CB', 'CD', 'DA', 'DB', 'DC']
```

permutations(items, i)

i는 option

**Idea : 순열은 12 랑 21이랑 같다고 생각함**



2. 조합

```python
from itertools import combinations 

items = ['A', 'B', 'C', 'D'] 
for i in range(1, len(items)): 
    print(list(map(''.join, combinations(items, i)))) 
# 조합을 만들려는 아이템과 조합의 수를 반드시 넘겨줘야한다.

>>['A', 'B', 'C', 'D']
['AB', 'AC', 'AD', 'BC', 'BD', 'CD']
['ABC', 'ABD', 'ACD', 'BCD']
```

combinations(items, i)

i는 필수 - **조합으로 구하는 갯수가 필수적**임.



```python
from itertools import combinations

items = ['A', 'B', 'C', 'D'] 

for i in range(1, len(items)):
    print(list(map(''.join,combinations(items, i))))

    
>>['A', 'B', 'C', 'D']
['AB', 'AC', 'AD', 'BC', 'BD', 'CD']
['ABC', 'ABD', 'ACD', 'BCD']
```



## Python's Comprehension

- List Comprehension (LC)
- Set Comprehension (SC)
- Dict Comprehension (DC)
- Generator Expression (GE) == generator는 특별히 expression이라고 부름



### for문을 활용한 list comprehension

> [ 식 for 원소 in 리스트 if 문 ]

```python
>>> [i for i in range(5)]
[0, 1, 2, 3, 4]
```

위의 코드를 말로 풀면 다음과 같다.

| range(5) 안(in)에서 | 각각의(for) 원소(i)를 고르고 | 그 i를 리스트 안에 나타내라 |
| :------------------ | :--------------------------- | :-------------------------- |
| in range(5)         | for i                        | i                           |

예제

```python
>>> [i+5 for i in range(5)]
[5, 6, 7, 8, 9]
>>> [i*2 for i in range(5)]
[0, 2, 4, 6, 8]
```



### 단일 if문을 포함한 list comprehension

if 문은 for 문 뒤에 나오면 된다. 만약 range(5)에서 짝수만 리스트로 작성하려면 아래와 같이 하면 된다.

```python
>>> [i for i in range(5) if i % 2 == 0]
[0, 2, 4]
>>> [i for i in range(5) if i % 2 == 1]
[1, 3]
```

![img](README%20assets/%ED%94%84%EB%A1%9C%EB%94%A7001.png)



### if와 else문을 포함한 List Comprehension

if 문에 else를 추가하여 리스트를 생성할 수 있다. 만약에 [0,1,2,3,4] 중 짝수는 모두 리스트에 포함시키고 홀수일 경우에는 None을 리스트에 포함시키려고 한다면 아래와 같이 하면 된다.

```python
>>> [i if i % 2 == 0 else None for i in range(5) ]
[0, None, 2, None, 4]
```

else가 추가되는 경우에는 if~else문이 **i와 for 사이에** 위치하여야 한다는 점에 유의하기 바란다.



### 중첩 for문을 포함한 List Comprehension

for 문을 중첩하여 List Comprehension을 만들 수 있다. 1~5 사이의 숫자에 각각 7~9 숫자를 곱한 결과를 리스트에 나타내고 싶다면 아래와 같이 하면 된다.

```python
>>> [i*j for i in range(1,6) for j in range(7,10)]
[7, 8, 9, 14, 16, 18, 21, 24, 27, 28, 32, 36, 35, 40, 45]
```

for 문 뒤에 for 문을 계속 쓰는 경우 **앞의 for 문의 원소에 대해서 그 다음 for 문의 원소를 순차적으로 적용한 결과**가 리스트에 나타나게 된다. 상기 사례를 도식화해서 나타내면 아래와 같다.

![img](README%20assets/%ED%94%84%EB%A1%9C%EB%94%A7001_3Zs9WXs.png)



# set(집합)

### set(집합) - 기본

- set은 수학에서 이야기하는 집합과 비슷합니다.
- 순서가 없고, 집합안에서는 unique한 값을 가집니다.
- 그리고 mutable 객체입니다.
- REPL으로 여러가지를 확인해봅니다.
- 중괄호를 사용하는 것은 dictionary와 비슷하지만, key가 없습니다. 값만 존재합니다.

```python
>>> s = {3, 5, 7}
>>> s
{3, 5, 7}
>>> type(s)
<class 'set'>
```

- set(집합) 내부 원소는 다양한 값을 함께 가질 수 있지만, mutable한 값은 가질수 없습니다.

```python
>>> s = {"1", 3, 5, (1,3)}
>>> s
{(1, 3), 5, 3, '1'}
>>> s = {"1", 3, 5, [1,3]}
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
>>> s = {"1", 3, 5, {1,3}}
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'set'
>>> s = {"1", 3, 5, {1:1,3:3}}
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'dict'
>>> s = {"1", 3, 5, frozenset([1,3,4])}
>>> s
{5, 3, '1', frozenset({1, 3, 4})}
```

### 2. set(집합) 선언

- list나 dict의 경우 대괄호나 중괄호로 선언할 수 있었습니다만, set은 dict타입과 동일한 중괄호를 사용하므로, 중괄호만으로는 생성할 수 없습니다.
- set 생성자를 이용합니다.

```python
>>> s = {}
>>> type(s)
<class 'dict'>
>>> s = set()
>>> type(s)
<class 'set'>
>>> s
set()
```

- set 생성자에 iterable한 객체를 넣으면 변환하여 set을 만들어 줍니다.
- 물론 set생성자 없이 바로 중괄호 안에 값을 넣어도 됩니다.

```python
>>> s = set([1,3,5,7])
>>> s
{1, 3, 5, 7}
>>> p = {1, 3, 5, 7}
>>> p
{1, 3, 5, 7}
```

- 중복된 값은 자동으로 중복이 제거 됩니다.

```python
>>> s = {1, 5, 1, 1, 1, 3, 7}
>>> s
{1, 3, 5, 7}
```

- set(집합)은 순서가 없습니다. 어떤 값이 먼저 나올지 알 수 없습니다.

```python
>>> for i in {1, 2, 4, 8, 16,32}:
...     print(i)
... 
32
1
2
4
8
16
```

### 3. set(집합)의 in

- 다른 collection 타입과 동일하게 동작 합니다.

```python
>>> 2 in r
True
>>> 3 in r
False
>>> 3 not in r
True
```

### 4. set(집합)의 원소 추가

- 원소 추가는 `add` 메소드를 이용합니다.

```python
>>> k = {100, 105}
>>> k.add(50)
>>> k
{105, 50, 100}
>>> k.add(12)
>>> k
{105, 50, 100, 12}
```

### 5. set(집합)의 update

- dictionary의 update는 여러값을 수정 또는 추가할때 사용했습니다만, set은 중복은 자동으로 제거되고 수정이라는 개념보다, 여러데이터를 한번에 추가할 때 사용합니다.

```python
>>> k = {1, 2, 3}
>>> k.update([3, 4, 5])
>>> k
{1, 2, 3, 4, 5}
```

### 6. set(집합)의 원소 제거

- remove(item) : item에 해당하는 원소를 제거하고, 없으면 KeyError 발생

```python
>>> k = {1, 2, 3}
>>> k.remove(3)
>>> k
{1, 2}
>>> k.remove(3)
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
KeyError: 3
```

- discard(item) : item에 해당하는 원소를 제거하고, 없어도 에러발생하지 않음

```python
>>> k = {1, 2, 3}
>>> k.discard(3)
>>> k
{1, 2}
>>> k.discard(3)
>>> k
{1, 2}
```

### 7. set(집합)의 복사

- set 내부의 값은 불변의 값만 들어올 수 있기때문에.. 얕은 복사와 깊은 복사의 구분이 필요 없을것 같지만... 일단 set의 메소드인 copy는 얕은 복사에 해당합니다.

```python
>>> s = {1, 3, 5}
>>> t = s.copy()
>>> s
{1, 3, 5}
>>> t
{1, 3, 5}
>>> id(s)
4334668264
>>> id(t)
4334666696
```

- dictionary 처럼 생성자로 복사할 수 있습니다.

```python
>>> s = {1, 3, 5}
>>> t = set(s)
>>> s
{1, 3, 5}
>>> t
{1, 3, 5}
>>> id(s)
4334666248
>>> id(t)
4334667144
```

### 8. set(집합) 연산 - 연산자

- `|` - 합집합 연산자

```python
>>> a = {1, 2, 3, 4, 5}
>>> b = {3, 4, 5, 6, 7}
>>> c = a | b
>>> a
{1, 2, 3, 4, 5}
>>> b
{3, 4, 5, 6, 7}
>>> c
{1, 2, 3, 4, 5, 6, 7}
```

- `&` : 교집합 연산자

```python
>>> a = {1, 2, 3, 4, 5}
>>> b = {3, 4, 5, 6, 7}
>>> c = a & b
>>> a
{1, 2, 3, 4, 5}
>>> b
{3, 4, 5, 6, 7}
>>> c
{3, 4, 5}
```

- `-` : 차집합 연산자

```python
>>> a = {1, 2, 3, 4, 5}
>>> b = {3, 4, 5, 6, 7}
>>> c = a - b
>>> a
{1, 2, 3, 4, 5}
>>> b
{3, 4, 5, 6, 7}
>>> c
{1, 2}
```

- `^` : 대칭차집합 연산자(합집합 - 교집합)

```python
>>> a = {1, 2, 3, 4, 5}
>>> b = {3, 4, 5, 6, 7}
>>> c = a ^ b
>>> a
{1, 2, 3, 4, 5}
>>> b
{3, 4, 5, 6, 7}
>>> c
{1, 2, 6, 7}
```

- `|=, &=, -=, ^=` : `=` 과 조합함으로써 연산과 동시에 할당합니다.
- id 또한 변경되지 않습니다.

```python
>>> a = {1, 2, 3, 4, 5}
>>> b = {3, 4, 5, 6, 7}
>>> a |= b
>>> a
{1, 2, 3, 4, 5, 6, 7}
>>> b
{3, 4, 5, 6, 7}
>>> a = {1, 2, 3, 4, 5}
>>> b = {3, 4, 5, 6, 7}
>>> id(a)
4334668040
>>> a &= b
>>> a
{3, 4, 5}
>>> id(a)
4334668040
>>> 
```

### 9. set(집합) - 연산메소드

- union - 합집합

```python
>>> a = {1, 2, 3, 4, 5}
>>> b = {3, 4, 5, 6, 7}
>>> c = a.union(b)
>>> a
{1, 2, 3, 4, 5}
>>> b
{3, 4, 5, 6, 7}
>>> c
{1, 2, 3, 4, 5, 6, 7}
```

- intersection - 교집합

```python
>>> a = {1, 2, 3, 4, 5}
>>> b = {3, 4, 5, 6, 7}
>>> c = a.intersection(b)
>>> a
{1, 2, 3, 4, 5}
>>> b
{3, 4, 5, 6, 7}
>>> c
{3, 4, 5}
```

- difference - 차집합

```python
>>> a = {1, 2, 3, 4, 5}
>>> b = {3, 4, 5, 6, 7}
>>> c = a.difference(b)
>>> a
{1, 2, 3, 4, 5}
>>> b
{3, 4, 5, 6, 7}
>>> c
{1, 2}
```

- symmetric_difference : 대칭차집합 연산자(합집합 - 교집합)

```python
>>> a = {1, 2, 3, 4, 5}
>>> b = {3, 4, 5, 6, 7}
>>> c = a.symmetric_difference(b)
>>> a
{1, 2, 3, 4, 5}
>>> b
{3, 4, 5, 6, 7}
>>> c
{1, 2, 6, 7}
```

### 10. set(집합) - 기타 메소드

- issubset : 부분집합 여부 확인

```python
>>> a = {1, 2, 3, 4, 5}
>>> b = {1, 2, 3}
>>> a.issubset(b)
False
>>> b.issubset(a)
True
```

- issuperset : issubset과 반대 superset인지 확인

```python
>>> a = {1, 2, 3, 4, 5}
>>> b = {1, 2, 3}
>>> a.issuperset(b)
True
>>> b.issuperset(a)
False
```

- isdisjoint : 교집합이 없으면 True, 있으면 False

```python
>>> a = {1, 2, 3}
>>> b = {4, 5, 6}
>>> a.isdisjoint(b)
True
>>> c = {1, 2, 3}
>>> d = {3, 4, 5}
>>> c.isdisjoint(d)
False
```