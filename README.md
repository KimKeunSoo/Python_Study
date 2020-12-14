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

