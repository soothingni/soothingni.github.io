# Variables


```python
def calc(a, b, op):
    if op == '+': result = a + b
    elif op == '-': result = a - b
    elif op == '*': result = a * b
    elif op == '/': result = a / b
    else: result = None
    return result
```


```python
calc(1, 3, '*')
```




    3



## 지역변수(local)과 전역변수(global)


```python
def spam(eggs):
    eggs.append
    print(id(eggs))
    eggs = [2, 3]
    print(id(ham))
    print(id(eggs))
    
ham = [0]
print(spam(ham))
print(ham)

#리스트 변수의 경우 값이 아니라 주솟값을 전달하기 때문; call by value vs. call by reference
```

    2396430417288
    2396430417288
    2396430417800
    None
    [0, 1]
    

## 재귀함수


```python
def factorial(n):
    if n == 1:
        return 1
    #탈출 조건을 필수적으로 만들어주어야 한다.
    else:
        return n * factorial(n-1)
```


```python
factorial(5)
```




    120



## 가변인수


```python
def variable_test(a, b, *args):
    print(type(args))
    return a + b + sum(args)

print(variable_test(1, 2))
print(variable_test(1, 2, 3, 4, 5))
```

    <class 'tuple'>
    3
    <class 'tuple'>
    15
    


```python
#언패킹할 때에도 *(asterisk) 까먹지말기
def variable_test2(*args):
    x, y, *z = args
    print(type(z))
    return x, y, z

print(variable_test2(1, 2, 3))
```

    <class 'list'>
    (1, 2, [3])
    


```python
#키워드 가변인수
def variable_test3(**kwargs):
    print(kwargs)
    print('The first variable is {first}'.format(**kwargs))
    print('The second variable is {second}'.format(**kwargs))
    print('The third variable is {third}'.format(**kwargs))
    
variable_test3(first = 1, second = 3, third = 5)
```

    {'first': 1, 'second': 3, 'third': 5}
    The first variable is 1
    The second variable is 3
    The third variable is 5
    


```python
#가변인수는 키워드 인수를 모두 선언한 후에! (전에는 안된다)
def kwargs_test(*args, a, b):
    return a + b + sum(args)
kwargs_test(1, 2, 3, 4, 5)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-19-2c3a6ebd30cf> in <module>
    ----> 1 kwargs_test(1, 2, 3, 4, 5)
    

    TypeError: kwargs_test() missing 2 required keyword-only arguments: 'a' and 'b'


##### 튜플


```python
tup1 = (1, 2, 3)
tup2 = (4, 5, 6)
```


```python
tup1[0]
```




    1




```python
tup1[0] = 3
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-22-ac49bb8ca6c7> in <module>
    ----> 1 tup1[0] = 3
    

    TypeError: 'tuple' object does not support item assignment



```python
tup1 + tup2
```




    (1, 2, 3, 4, 5, 6)




```python
del tup1
```


```python
tup1
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-28-359c5fbf330f> in <module>
    ----> 1 print(tup1)
    

    NameError: name 'tup1' is not defined


##### 딕셔너리 


```python
dict1 = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}
```


```python
dict1['School'] = 'DPS School'
```


```python
dict1
```




    {'Name': 'Zara', 'Age': 7, 'Class': 'First', 'School': 'DPS School'}




```python
dict1.clear()
```


```python
dict1
```




    {}




```python
del dict1
```


```python
dict1
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-48-e36219336d90> in <module>
    ----> 1 dict1
    

    NameError: name 'dict1' is not defined



```python
dict1 = {'Name': 'Zara', 'Age': 7, 'Class': 'First', 'Name': 'Manni'}
```


```python
dict1
```




    {'Name': 'Manni', 'Age': 7, 'Class': 'First'}




```python
print("Value: %s" % dict1.items())
```

    Value: dict_items([('Name', 'Manni'), ('Age', 7), ('Class', 'First')])
    


```python
print("Value: %s" % dict1.keys())
```

    Value: dict_keys(['Name', 'Age', 'Class'])
    


```python
print ("Value : %s" %  dict1.get('Age'))
print ("Value : %s" %  dict.get('Sex', "NA"))
#존재하지 않는 값 확인할 때 유용
```

    Value : 7
    Value : NA
    


```python
dict1 = {'Name': 'Zara', 'Age': 7};
dict2 = {'Name': 'Mahnaz', 'Age': 27};
dict3 = {'Name': 'Abid', 'Age': 27};
dict4 = {'Name': 'Zara', 'Age': 7};
```

##### 문자열


```python
#문자열 사이즈 확인하기
import sys
print(sys.getsizeof('a'), sys.getsizeof('abc'), sys.getsizeof('abcde'),)
```

    50 52 54
    


```python
int_value = 2
print('결과는 ' + int_value)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-72-e683a4b905aa> in <module>
          1 int_value = 2
    ----> 2 print('결과는 ' + int_value)
    

    TypeError: can only concatenate str (not "int") to str



```python
title = 'python for data analysis'
print(title.title())
```

    Python For Data Analysis
    


```python
title.isdigit()
```




    False




```python
title.startswith('a')
```




    False




```python
title.startswith('P')
```




    False




```python
#줄바꿈 표현
s = "I'm OK
I'm happy
See you"
print(s)
```


      File "<ipython-input-77-7e797437a23c>", line 2
        s = "I'm OK
                   ^
    SyntaxError: EOL while scanning string literal
    



```python
s = """I'm OK
I'm happy
See you"""
print(s)
```

    I'm OK
    I'm happy
    See you
    


```python
f = open('yesterday.txt', 'r')
yesterday_lyric = f.readlines()
f.close()

num_of_word = 0

for line in yesterday_lyric:
    lyric = line.lower()
    num_of_word += lyric.count('yesterday')

print('Number of words: %d' % num_of_word)
```

    Number of words: 9
    


```python
yesterday_lyric
```




    ['Yesterday all my troubles\n',
     'seemed so far away.\n',
     'Now it looks\n',
     "as though they're here to stay.\n",
     'Oh, I believe in yesterday.\n',
     '\n',
     "Suddenly I'm not half\n",
     'the man I used to be.\n',
     "There's a shadow hanging over me.\n",
     'Oh, yesterday came suddenly.\n',
     '\n',
     'Why she had to go,\n',
     "I don't know,\n",
     "she wouldn't say.\n",
     'I said something wrong,\n',
     'now I long for yesterday.\n',
     '\n',
     'Yesterday love was\n',
     'such an easy game to play.\n',
     'Now I need a place to hide away.\n',
     'Oh, I believe in yesterday.\n',
     '\n',
     'Why she had to go,\n',
     "I don't know,\n",
     "she wouldn't say.\n",
     'I said something wrong,\n',
     'now I long for yesterday.\n',
     '\n',
     'Yesterday love was\n',
     'such an easy game to play.\n',
     'Now I need a place to hide away.\n',
     'Oh, I believe in yesterday.\n',
     '\n',
     'Mm mm mm mm mm mm mm\n',
     '\n']




```python

```
