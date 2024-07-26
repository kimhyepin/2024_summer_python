# 자료구조
1. list []
- .index(”누구누구”) → 누구누구의 인덱스를 알려줌
- .append(”누구누구”) → 누구누구를 리스트의 마지막에 넣어줌
- .insert(n, “누구누구”) → 누구누구를 리스트의 인덱스 n 에 추가해줌
- .pop() → 리스트의 마지막 요소를 빼줌
- .count(”누구누구”) → 리스트에 누구누구가 몇 번 있는지 알려줌

```python
subway = ["유재석", "조세호", "박명수"]
print(subway.index("조세호")) # 조세호의 index를 알려줌

subway.append("하하") 
print(subway) # 하하를 subway list 에 추가할 수 있음 (마지막에)

subway.insert(1, "정형돈")
print(subway) # 인덱스 1에 정형돈이 추가됨 
# ["유재석", "정형돈", "조세호", "박명수" ,"하하"]

print(subway.pop()) # 맨 뒤에 있는 하하를 뺌
print(subway)
# print(subway.pop()) # 그 앞에 있는 박명수를 뺌
# print(subway)
# print(subway.pop()) # 그 앞에 있는 조세호를 뺌
# print(subway)

# 같은 이름의 사람이 몇명이나 있는지 확인
subway.append("유재석")
print(subway) #['유재석', '정형돈', '조세호', '박명수', '유재석']

print(subway.count("유재석")) # 2
```

```python
# 정렬도 가능
num_list = [5,4,2,3,10]
num_list.sort()
print(num_list) 

# 뒤집기도 가능
num_list.reverse()
print(num_list)

# 모두 지우기도 가능 
num_list.clear()
print(num_list)

# 결과 : 

# [2, 3, 4, 5, 10]
# [10, 5, 4, 3, 2]
# []
```

2. dictionary {key:value} 
- key 가져올때 [] 와 .get() 의 차이점 보기

→ [] 는 없는 키 가져오면 바로 오류

→ .get() 은 없는 키 가져오면 none 반환 

```python
# 캐비넷 3번은 유재석이 쓰고 있고, 100번은 김태호가 쓰고 있음 
cabinet = {3: "유재석", 100:"김태호"}
print(cabinet[3])
# print(cabinet[5]) # 없는 키 주면 none 을 반환하는 게 아니라 오류 띄우고 code 실행 종료됨

print(cabinet.get(99)) # get으로 키 받아오면 없는 키 주어도 오류 띄우는 게 아니라 none 반환하고 뒤의 코드 이어서 실행해줌
print(cabinet.get(99,"사용가능")) # 키가 없을때 none 말고 지정된 값 주고 싶으면 이렇게 하면됨! 99 키가 존재하면 그에 대한 value 뱉고 아니라면 사용가능 이라는 말 뱉음
```

```python
# 딕셔너리에 값 추가 
cabinet = {3: "유재석", 100:"김태호"}
cabinet["A-30"] = "하하"
print(cabinet) # {3: '유재석', 100: '김태호', 'A-30': '하하'}
```

```python
# 딕셔너리에 값 삭제 
cabinet = {3: "유재석", 100:"김태호"}
del cabinet[3]
print(cabinet)  # {100: '김태호'}
```

```python
cabinet = {3: "유재석", 100:"김태호"}

# key 들만 출력
print(cabinet.keys())
# 결과 : dict_keys([3, 100])

# value 들만 출력
print (cabinet.values())
# 결과 : dict_values(['유재석', '김태호'])

# key, value 쌍으로 출력
print(cabinet.items())
# 결과 : dict_items([(3, '유재석'), (100, '김태호')])

print(cabinet.clear())
# 다 지워짐 ! 
# 결과 : None 
```

3. tuple () 
- 요소를 바꿀 수 없다는 특징, 그럼 왜쓸까? → 속도가 리스트보다 빠름

```python
age = (20, 30, 40, 50)
print(age[3])

(name, age, hobby) = ("김종국", 20, "코딩")
print(name, age, hobby)
```

4. set {} , set([])
- 중복안됨, 순서 없음

→ 집합에서 할 수 있는 모든 것들을 할 수 있음 (교집합, 합집합, 차집합, 값추가, 값제거) 

```python
java = {"유재석", "김태호", "양세형"}
python = set(["유재석", "김혜빈"])

# 교집합 (python 과 java 모두 할 수 있는 사람)
print (java & python) # {'유재석'}

# 합집합 (python 과 java 둘 중 하나라도 할 수 있는 사람)
print (java | python) # {'양세형', '유재석', '김혜빈', '김태호'}

# 차집합 (java 할 수 있지만 python 못하는 사람)
print (java - python) # {'양세형', '김태호'}

# add 와 remove 도 모두 가능함 
```
### colection 
1. deque <br>
&rarr;  Stack (LIFO(Last In First Out))과 Queue (FIFO(First In First Out))를 지원하는 모듈

```python
from collections import deque

deque_list = deque()
for i in range(5):
    deque_list.append(i)
print(deque_list)  

deque_list.appendleft(10)
print(deque_list)  
..
..
deque([0, 1, 2, 3, 4])
deque([10, 0, 1, 2, 3, 4])
```

Deque: Linked List 특성을 지원 <br>
Linked List란? 데이터를 연결하여 저장하는 방식
```python
from collections import deque

deque_list = deque([10, 0, 1, 2, 3, 4])

deque_list.rotate(2)
print(deque_list)  # deque([3, 4, 10, 0, 1, 2])

deque_list.rotate(2)
print(deque_list)  # deque([1, 2, 3, 4, 10, 0])

print(deque_list)  # deque([1, 2, 3, 4, 10, 0])
print(deque(reversed(deque_list)))  # deque([0, 10, 4, 3, 2, 1])

deque_list.extend([5, 6, 7])
print(deque_list)  # deque([1, 2, 3, 4, 10, 0, 5, 6, 7])

deque_list.extendleft([5, 6, 7])
print(deque_list)  # deque([7, 6, 5, 1, 2, 3, 4, 10, 0, 5, 6, 7])
```
<br>
&rarr; deque 왜 쓰지 ??! : deque가 더 빠름 (2배 정도)<br>
즉, stack이나 queue 를 쓸 일 있으면 deque 쓰는것이 시간 면에서 효율적<br><br>

2. orderdict <br>
&rarr; 순서가 있는 dict, 입력한 순서대로 출력 &harr; 일반 dict : 입력한 순서와 상관없이 출력

```python
# 일반 딕셔너리
d = {}
d['x'] = 100
d['y'] = 200
d['z'] = 300
d['l'] = 500

print("일반 dict 출력:")
for k, v in d.items():
    print(k, v)

from collections import OrderedDict

# OrderedDict
od = OrderedDict()
od['x'] = 100
od['y'] = 200
od['z'] = 300
od['l'] = 500

print("\nOrderedDict 출력:")
for k, v in od.items():
    print(k, v)
..
..

일반 dict 출력:
x 100
y 200
z 300
l 500

OrderedDict 출력:
x 100
y 200
z 300
l 500

# 왜 똑같이 나오지 ? : python 3.7 이후로는 ~ 
```

```python
from collections import OrderedDict


d = {'x': 100, 'y': 200, 'z': 300, 'l': 500}

# key 를 기준으로 정렬
for k, v in OrderedDict(sorted(d.items(), key=lambda t: t[0])).items():
    print(k, v + '\n')

# vaule 을 기준으로 정렬
for k, v in OrderedDict(sorted(d.items(), key=lambda t: t[1])).items():
    print(k, v)
..
..
l 500
x 100
y 200
z 300

x 100
y 200
z 300
l 500
```

3. default dict <br>
```python
from collections import defaultdict

# 기본값을 0으로 설정한 defaultdict 생성
d = defaultdict(lambda: 0)

# key-value 할당
d["a"] = 1
d["b"] = 2
d["c"] = 3

# 할당된 값 출력
print("할당된 쌍:")
for k, v in d.items():
    print(k, v)

# 존재하지 않는 키를 조회할 경우 기본값 출력
print("\n존재하지 않는 쌍:")
print(d["first"])
..
..

할당된 쌍:
a 1
b 2
c 3

존재하지 않는 쌍:
0
```
4. counter <br>
Counter는 Sequence형 데이터 타입의 요소 개수를 세는 기능 <br>
파이썬의 다양한 데이터 타입에 적용 가능하며, dict 형태로의 반환

```python
from collections import Counter

c = Counter()  # 빈 counter 생성
c = Counter('dallhad')  

print(c)  # Counter({'a': 3, 'l': 2, 'd': 1, 'h': 1})
```