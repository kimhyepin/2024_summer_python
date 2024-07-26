# 👩‍💻 Pythonic code 

### 왜 필요할까?

효율적으로 코드 표현 가능 &rarr; 인간의 시간이 컴퓨터의 시간보다 중요! <br>
남 코드에 대한 이해도 

### List comprehensions 
&rarr; 기존 list를 사용하여 새로운 지능형 list 생성 <br>
&rarr; (내가 주로 사용하는) for + append 보다 속도가 빠름<br><br>

``` python
new_list = [expression for item in iterable if condition]
```

expression: 각 항목에 적용되는 표현식(계산 또는 변형)<br>
item: 반복되는(iterable) 항목들에 대한 변수<br>
iterable: 순회 가능한 객체(리스트, 튜플, 문자열 등)<br>
condition (선택사항): 조건문으로, 해당 조건을 만족하는 경우에만 표현식이 적용됨<br> <br>

```python
result = [i for i in range(10) if i % 2 == 0 ]
..
..
result
[0, 2, 4, 6, 8]
```

&rarr; 우선 item 이 i이고 range(10) 까지 for 문을 도므로 0 1 2 3 4 5 6 7 8 9 가 i에 담기고 실제로 리스트에 추가할 항목 (expression) 도 i니까 이게 그대로 담기는데 조건상 나머지가 0인 요소 만 담겨서 0 2 4 6 8 이 담긴 새로운 list가 list comprehension으로 생성된 것이다. 따라서 result 를 print 하면 [0, 2, 4, 6, 8] 이 나오게 된다. 

```python
words = "The quick brown for jumps over the lazy dog".split()
print(words)

new_lst = [[w.upper(), w.lower(), len(w)]for w in words] 
print (new_lst)
..
..
['The', 'quick', 'brown', 'for', 'jumps', 'over', 'the', 'lazy', 'dog']
[['THE', 'the', 3], ['QUICK', 'quick', 5], ['BROWN', 'brown', 5], ['FOR', 'for', 3], ['JUMPS', 'jumps', 5], ['OVER', 'over', 4], ['THE', 'the', 3], ['LAZY', 'lazy', 4], ['DOG', 'dog', 3]]
```
```python
case_1 = ['A', 'B', 'C']
case_2 = ['D', 'E', 'A']

result = [i + j for i in case_1 for j in case_2]
print(result)

# 같은 결과
result02 = [] 
for i in case_1:
    for j in case_2:
        result02.append(i+j)
print(result02)
```

```python
case_1 = ['A', 'B', 'C']
case_2 = ['D', 'E', 'A']

result = [[i + j for i in case_1] for j in case_2]
result = [element for x in result for element in x]
print(result)

# 같은 결과 
result02 = []
for j in case_2:
    for i in case_1:
        result02.append(i+j)
print(result02)
```

### Enumerate & Zip

* Enumerate 란 ?
<br> 리스트의 값을 추출할 때 인덱스를 붙여 함꼐 출력하는 방법
```python
for i, v in enumerate(['tic', 'tac', 'toe']) :
    print(i, v)
..
.. 
0 tic
1 tac
2 toe
```

* zip이란?
<br> 두개의 list의 값을 병렬적으로 추출
```python
result = [sum(x) for x in zip((1, 2, 3), (10, 20, 30), (100, 200, 300))]
print(result)
..
..
[111, 222, 333]
```
&rarr; 만약에.. result = [x for x in zip((1, 2, 3), (10, 20, 30),  (100, 200, 300))] 였으면 [(1, 10, 100), (2, 20, 200), (3, 30, 300)] 이렇게 나옴 ! 

```python
alist = ['a1', 'a2', 'a3']
blist = ['b1', 'b2', 'b3']

for i, (a, b) in enumerate(zip(alist, blist)):
    print(i, a, b)  # index, alist[index], blist[index] 가 print ! 
```
