# 1. Python language

## 1.1 encoding

- When you write words and/or numbers, they need to be stored on the disk. 

```textile
hello123       0101011100100011
```

- codebook 

```textile
你          0100010001
R           1000100010
9           0100000100
```

- using software user.text

```python
你          0100010001
R           1000100010
9           0100000100
```

## 1.2 codebook

There are several codebooks in the computer science. 

When you write the file, **remember which codebook you used**. If you use the incorrect codebook to open the same file, it will not work and will display garbled text.

- Writing Python code (usually use UTF-8 encoding)

```python
print("hello world")
```

- Python Interpreter will use UTF-8 to open file

### 1.2.1 ASCII

It is a very old codebook (created by USA)

It uses 1byte (8 bits) structure, so only 256 results

```textile
NUL   00000000
@     01000000
```

```textile
default in Python2
```

### 1.2.2 gbk and gb2312

GB-2312, China (1980)

GBK, GB-2312's extension, includes other countries' words (1995)

### 1.2.3 unicode

- ucs2, 2 bytes structure 2**16 = 65535 

- ucs4, 4 bytes structure 2**32 = 4294967296

```python
ex: 

中 in ucs2 = 01000000 01010001
中 in ucs4 = 00000000 00000000 01000000 01010001
```

```textile
cons in ucs4: waste memory usage
```

### 1.2.4 utf-8

```textile
default in Python3
```

```textile
in ZH, 1 words == 3 bytes
```

### 1.2.5 Python

```python
word = 'hello world'           # string, unicode 
data = name.encode('utf-8')    # byte, utf-8
print(data)
```

When storing file or transferring file, string is not allowed. So, converting to byte before storing or transferring. 

```python
word = 'hello world'

# open file
file = open("xxx.txt", mode='ab')

# write word into file
file.write(word.encode("utf-8"))

# close file
file.close() 
```

```python
data = 'hello'
v1 = data.encode('utf-8')
print(v1) # 10001011 0000111 ...

text = v1.decode("utf-8") 
print(text) # hello
```

## 1.3 output (print)

```python
print("hello world")
# hello world
```

```python
## search png files in your_folder and print them
import os

for item in os.listdir("./your_folder"):
    if item.endswith('png'):
        print(item)
```

## 1.4 variable

Rule: giving **useful** name to variable

```python
# if you want to store someone's name in a variable
name = "Brian"

# DON'T use: 
n = "Brian"
```

- special rules:
1. variable only contains: Words, Numbers, _  

```python
a   = 'hello'
a0  = 'hello'
a_0 = 'hello'
```

2. cannot start with a number

```python
0 = "hello" # error
```

3. cannot use Python keywords

```python
and, as, assert, break, class, continue, def, del, elif, if, else, 
except, exec, finally, for, from, global, import, in, is, lambda, 
not, or, pass, print, return, try, while, with, yield,... 
```

```textile
global var = Upper words (DATA_LIST), local var = lower words (data_list)

function name = def name_info
Class name = GetInfo
```

## 1.5 comment

```python
# what is this line meaning (single line)
"""
what is this function meaning (multiple lines)
"""
```

## 1.6 input

```python
xxx = input('enter your number')
```

Note: input value always = "**string**" not "int"

## 1.7 basic knowledge

### 1.7.1 decimal / binary / hex...

for computer structure, it only uses **binary** 

```textile
0 0101 00001111...
```

```textile
decimal -- binary
        -- hex
```

- in python: 

only decimal is "**int**", the others are "**string**"

```python
## decimal to others
data = 238 

binary = bin(238) # "0b11101110"

oc = oct(238) # "0o356" 

he = hex(238) # "0xee"
```

```python
## others to decimal

d1 = int('0b11101110', base=2) # 238

d2 = int('0o356', base=8) # 238

d3 = int('0xee', base=16) # 238
```

### 1.7.2 unit in computer

- bit: 1

- byte: 8 bits (00001111)

- KB (kilobyte): 1024 bytes

- MB (megabyte): 1024 KB 

- GB (gigabyte): 1024 MB

- TB (terabyte): 1024 GB

# 2. Data types

## 2.1 int / float

```python
19
0 
1.222
```

```python
200 + 1
200 - 1
200 * 1 
200 / 1
200 % 1
```

```python
v1 = 0.1
v2 = 0.2

v3 = v1 + v2 
print(v3) # 0.30000000004 # it is ok
```

```python
# more accuracy
import decimal 

v1 = decimal.Decimal('0.1')
v2 = decimal.Decimal('0.2')

v3 = v1 + v2 
print(v3) # 0.3
```

use **round()**  to setup the point number you want 

```python
a = 1.333333
b = round(a, 2)
print(b) # 1.33
```

for infinity: 

```python
a = float('inf')
b = float('-inf')
```

## 2.2 string (str)

```python
for special
data 
text = data.format() / data.join() # 2.2.2 and 2.2.9
text = data.upper() / data.lower()
text = data.isdecimal()
text = data.startswith() / data.endswith()
text = data.strip() / data.lstrip() / data.rstrip()
text = data.replace()
text = data.split()
text = data.center() / data.rjust() / data.ljust
text = data.zfill()

for universal
data
text = len(data)
text = data[x] / data[x:y]
loop: 
for text in data
```

### 2.2.1 definition

**It is immutable**

```python
# single line: 
a = 'hello'
a = "hello"

# multiple lines:
m = """ hello """
m = ''' hello '''
```

```python
## it can connect
a = 'hello'
b = 'boy'
c = a + b # helloboy

## multiple times repeat 
a = 'hello'
b = a * 3
print(b) # hellohellohello
```

### 2.2.2 format (3 ways)

- popular (fomat)

```python
text = 'hello my name is {0}'.format("brian")
print(text) # hello my name is brain

text = 'hello my name is {0}. I am {1} years old'.format('brian', 18)
print(text) # hello my name is brian. I am 18 years old

text = '{xx} is boy, {yy} is girl, {zz} is girl.'
word = text.format(xx='Joy', zz='Amy', yy='Cindy')
print(word) # Joy is boy, Cindy is girl, Amy is girl.
```

- popular (f) 

```python
name = 'brian'
age = '18'
text = f'my name is {name}, i am {age} years old'
print(text) # my name is brian, i am 18 years old
```

NOTE: most after python 3.6

- not popular (%)

```python
text = 'hello my name is %s' %(brian)
print(text) # hello my name is brain
```

### 2.2.3 upper / lower

```textile
NOTE: using word.isupper() to check the word is upper or not
```

```python
name = 'root'
up = name.upper()
print(up) # ROOT
```

```python
name = "ROOT"
low = name.lower()
print(low) # root
```

### 2.2.4 isdecimal

it uses to check string contains **all int** or not

```python
data = '12'
check = data.isdecimal()
print(check) # True
```

```python
data = 'a2'
check = data.isdecimal()
print(check) # False
```

### 2.2.5 startwith / endwith

they use to check string uses "xxx" to start or "xxx" in the end. 

```python
name = "hello world"
v1 = name.startswith('hello') # True
v2 = name.endswith('hello') # False
```

```python
address = input('input your address')
if address.startswith('200'):
    print("house number is 200")
else: 
    print('house number is not 200')
```

```python
file = 'xxxx.png'
if file.endswith('png')
    print('it is a picture')
else: 
    print('it is not a picture')
```

### 2.2.6 (' '/ '\n' / '\t') / lstrip / rstrip

```textile
remove: space / change line 
```

```python
name = ' USA '

v1 = name.strip() # 'USA'

v2 = name.lstrip() # 'USA '

v3 = name.rstrip() # ' USA'
```

```python
name = input('enter your name') 
name = name.strip()

if name = "":
    print("cannot enter space")
else:
    print(name)

############################### or ("" == False)
if name: 
    print(name)
else:
    print("cannot enter space")
```

```python
a = " apple is good"
b = a.strip()
print(b) # "apple is good" 
# "strip" will not remove the whitespace between 2 words
```

### 2.2.7 replace

```python
text = 'hello world'
data = text.replace('hello','great')

print(data) # 'great world'
```

### 2.2.8 split

the string will be a "**list**" after split

```python
file_name = 'image 07.png'
data = file_name.split('.')
print(data[0]) # 'image 07'
print(data[1]) # 'png'
```

### 2.2.9 join

```python
# 1. +
v1 = 'usa'
v2 = 'china'
text = v1 + ' and ' + v2
print(text) # 'usa and china'
```

```python
# 2. format
v1 = 'usa'
v2 = 'china'
text = '{} and {}'.format(v1,v2)
print(text) # 'usa and china'
```

```python
# 3. join (list)
data_list = ['usa', 'china', 'germany']
text = "_".join(data_list)
print(text) # 'usa_china_germany'

#########
# error
data_list = ['usa', 1]
text = ''.join(data_list)
print(text) # error 
```

**Note:** if using "join" to connect. **All** elements in the list must be "string"

### 2.2.10 center / ljust / rjust

fill enough length 

```python
name = 'brian'
text = name.center(9,"*")
print(text) # '**brian**'
```

```python
name = 'brian'
text = name.ljust(9,"+")
print(text) # 'brian++++'
```

```python
name = 'brian'
text = name.rjust(9,'-')
print(text) # '----brian'
```

### 2.2.11 zfill

fill enough length with "**0**"

```python
name = 'brian'
text = name.zfill(7)
print(text) # '00brian'
```

```python
data = '0100'
binary = data.zfill(8)
print(data) # '00000100'
```

### 2.2.12 len

calculate lenght

```python
name = 'brian'
result = len(name)
print(result) # 5
```

### 2.2.13 index / slice

- index

```python
text = 'i want to learn python'
print(text[0]) # 'i'
print(text[1]) # ' '(space)
print(text[2]) # 'w'
print(text[-1]) # 'n'
```

note: cannot exceed the max length

- slice

```python
text = 'i want to learn python'
print(text[0:3]) # 'i w'
print(text[2:6]) # 'want'
print(text[10:-1]) # 'learn pytho'
print(text[:]) # 'i want to learn python'
```

### 2.2.14 loop

- while 

```python
data = 'i want to learn python'
index = 0
while index < len(data):
    char = data[index]
    print(char)
    index += 1
```

- for

```python
data 'i want to learn python'
for item in data:
    print(item)
```

## 2.3 boolean

```python
1 > 2 (False)
2 > 1 (True)
```

- int: 0 to False, others to True

```python
print(bool(0)) # False
print(bool(1)) # True
print(bool(200)) # True
```

- string: empty to False, others to True

```python
print(bool("")) # False
print(bool(" ")) # True
print(bool("s")) # True
```

```python
0, '', [], (), {}, None --> False
others = True
```

```python
## putting bool in the if or loop
if True:
    pass
while True:
    pass
```

```python
## convert to True or False
if "s":  # (True)
    pass

if "": # (False)
    pass

if None: # (False)
    pass
```

## 2.4 list

```python
for special 
data
data.append()
data.insert(x,y) # x == place , y == value
data.remove() / data.pop() or v1 = data.pop()
data.clear()
data.sort() / data.reverse()
text = data.count()
data.extend()

for universal 
data
text = len(data)
text = data[x] / data[x:y]
loop: 
for text in data
```

### 2.4.1 definition

**It is mutable and ordered**

elements can be different data types in the list

```python
[0, 'usa', True]
```

- embed

```python
data = [0, 11, 'usa', ['a', 2], 232, False]

print(data[0]) # 0
print(data[3][0]) # 'a'
```

### 2.4.2 append

```python
data = []
data.append(0)
data.append('usa')
print(data) # [0, 'usa']
```

```python
fruits = ["apple", "banana"]
foods = ["candy", "juice"]
fruits.extend(foods) # fruits = ["apple", "banana", "candy", "juice"]
# 4 elements in the list

fruits.append(foods) # fruits = ["apple", "banana", ["candy", "juice"]]
# 3 elements in the list
```

note: different with extend

### 2.4.3 insert

```python
data = ['apple', 'banana', 'candy']
data.insert(1,'fish')
print(data) # ['apple', 'fish', 'banana', 'candy']
```

### 2.4.4 remove

```python
data = ['apple', 'banana', 'candy']
data.remove('apple')
print(data) # ['banana', 'candy']

#######
data.remove('fish') # error (elements not exist)
```

```python
# little lottery 
import random

# create a list to store 200 people
people = []
for i in range(1,201):
    name = 'people '.format(i)
    people.append(name)

# randomly select first lucky people
lucky = random.choice(people)
print(f"first lucky people is {lucky}")

# remove from the list
people.remove(lucky)

# select second lucky people
lucky = random.choice(people)
print(f"second lucky people is {lucky}")
```

### 2.4.5 pop

```python
fruits = ['apple', 'banana', 'candy']
fruits.pop(1)
print(fruits) # ['apple', 'candy']
```

```python
fruits = ['apple', 'banana', 'candy']
fruits.pop() # pop last one
print(fruits) # ['apple', 'banana']
```

```python
fruits = ['apple', 'banana', 'candy']
data = fruits.pop(0) 
print(data) # 'apple'
```

### 2.4.6 clear

clear all list

```python
fruits = ['apple', 'banana', 'candy']
fruits.clear()
print(fruits) # []
```

### 2.4.7  sort / reverse

sort the elements

```python
number = [11,3,0,20]
number.sort()
print(number) # [0,3,11,20]
```

```python
number = [11,3,0,20]
number.sort(reverse=True)
print(number) # [20,11,3,0]

########
my_list = [1, 2, 3, 4, 5] 
my_list.reverse() 
print(my_list) 
# Output: [5, 4, 3, 2, 1]
```

```python
data = ['a', 'c', 'b']
data.sort()
print(data) # ['a', 'b', 'c']
```

### 2.4.8 count

```python
my_list = [1,2,3,4,5,2,3,2]
count = my_list.count(2)
print(count) # 3
```

### 2.4.9 extend

```python
fruits = ["apple", "banana"]
foods = ["candy", "juice"]
fruits.extend(foods) # fruits = ["apple", "banana", "candy", "juice"]
# 4 elements in the list

fruits.append(foods) # fruits = ["apple", "banana", ["candy", "juice"]]
# 3 elements in the list
```

### 2.4.10 len

```python
data = [11,2,3]
result = len(data)
print(result) # 3
```

### 2.4.11 index / slice

- index

```python
data = ['a', 2, 'c', 8, 10]

# get value 
print(data[0]) # 'a'
print(data[-1]) # 10

# modify
data[0] = 'b'
print(data) # ['b', 2, 'c', 8, 10]

# delete 
del data[2]
print(data) # ['a', 2, 8, 10]
```

- slice

```python
data = ['a', 2, 'c', 8, 10]

# get value
print(data[0:2]) # ['a', 2]

# modify 
data[0:2] = [0, 1, 2, 3]
print(data) #  [0, 1, 2, 3, 'c', 8, 10] 

# delete
del data[1:3]
print(data) # ['a', 8, 10]
```

### 2.4.12 loop (for)

```python
fruits = ["apple", "banana", "candy", "juice"]
for item in fruits:
    print(item)
```

## 2.5 tuple

```python
for universal
data
text = len(data)
text = data[x] / data[x:y]
loop: 
for text in data
```

### 2.5.1 definition

**It is immutable and ordered**

```python
v1 = (11,22,33)
v2 = (11,True,"a")
v3 = (11, (22,33), [22,'c'])
print(v3[1][1]) # 33

# elements in tuple cannot modify 
v3[0] = 1 # error
v3[-1][0] = 33 # correct (11, (22,33), [33,'c'])
```

**important info**

```python
v1 = (11,22) # tuple
v2 = (11,22,) # tuple
v3 = (33) ## int 33
v4 = (33,) # tuple 
```

```python
v1 = ((1),(2),(3))
v2 = (1,2,3)
v3 = ((1,),(2,),(3,))

# v1 = v2 != v3
```

### 2.5.2 public function

- length

```python
v1 = (1,'a', True)
result = len(v1)
print(result) # 3
```

- index (read only)

```python
v1 = (1,'a', True)
print(v1[0]) # 1
```

- slice (read only)

```python
v1 = (1,'a', True)
print(v1[0:2]) # (1, 'a')
```

## 2.6 dictionary (dict)

```python
for special
text = data.get(x)
key, values
items
dict_name.update({key:value}) # add new key-value pairs into the dict
dict_name.clear() # clear all key-value pairs

for universial 
data
text = len(data)
text = data[x] / data[x:y]
loop: 
for text in data
```

### 2.6.1 definition

**It is mutable and ordered (after python 3.6)**

```python
info = {'a':12, 'b':13}
```

- key-value pair

- key cannot be the same

```python
info = {'a':12, 'a':13}
print(info) # {'a':13}
```

- key must be "hashable"

```python
hashable = int, bool, str, tuple
unhashable = dict, list
```

- embed 

```python
info = {
    'k1': 123,
    'k2': (11,22),
    'k3': [11,22],
    'k4': [11,22,{'v1':33, 'v2':44}],
}
```

### 2.6.2 get

```python
info = {
    'name':'brian',
    'age': 18,
    'status': True,
    'hubby':['basketball','run']
}

# get by key
v1 = info.get('name')
print(v1) # 'brian'

v2 = info.get('email')
print(v2) # None / null

v3 = info.get('email', 'xxx') # if 'email' is not exist, v3 = 'xxx'
print(v3) # 'xxx'

v4 = info.get('age', 33)
print(v4) # 18
```

### 2.6.3 key, value

- key

```python
info = {
    'name':'brian',
    'age': 18,
    'status': True,
    'hubby':['basketball','run']
}

v1 = info.keys() # get a list
print(v1) # dict_keys(['name', 'age', 'status', 'hubby'])

for item in info.keys():
    print(item)

data = list(v1)
print(data) # ['name', 'age', 'status', 'hubby']
```

- value

```python
info = {
    'name':'brian',
    'age': 18,
    'status': True,
    'hubby':['basketball','run']
}

v1 = info.values() # get a list
print(v1) # dict_keys(['brian', 18, True, ['basketball','run']])

for item in info.values():
    print(item)

data = list(v1)
print(data) # ['brian', 18, True, ['basketball', 'run']]
```

### 2.6.4 items

```python
info = {
    'name':'brian',
    'age': 18,
    'status': True,
    'hubby':['basketball','run']
}

v1 = info.items() # get a list
print(v1) # dict_items([('name', 'brian'), ('age', 18), ('status', True), ('hubby', ['basketball', 'run'])])

for item in info.values():
    print(item)

data = list(v1)
print(data) # [('name', 'brian'), ('age', 18), ('status', True), ('hubby', ['basketball', 'run'])]
```

### 2.6.5 public function

- len

```python
info = {
    'name':'brian',
    'age': 18,
    'status': True,
    'hubby':['basketball','run']
}

data = len(info)
print(data) # 4
```

- index 

```python
info = {
    'name':'brian',
    'age': 18,
    'status': True,
    'hubby':['basketball','run']
}

v1 = info['name']
print(v1) # 'brian'

v2 = info['email'] # error
```

note: to get the values from key (recommend to use **get**)

```python
info = {
    'name':'brian',
    'age': 18,
    'status': True,
    'hubby':['basketball','run']
}

# modify 
info['age'] = 22

# add
info['email'] = 'xxx'

# delete
del info['name'] 

## note: if key is not exist, del shows error
```

## 2.7 set

```python
for special 
data
data.add()
data.discard() 
data.intersection() = (a & b) / data.union() = (a | b) 
/ data.difference() = (a - b)
data.clear() # clear all data in the set

for universal 
text = len(data)
loop: 
for word in text 
if a in b
```

### 2.7.1 definition

**It is mutable and unordered**

```python
v1 = {1,2,3}
```

```python
v1 = {1,2,3}
v1.add(4)
print(v1) # {1,2,3,4}
```

- no repeat

```python
v1 = {1,2,3}
v1.add(1)
print(v1) # {1,2,3}
```

- element mush hashable

```python
set is unhashable
```

when to use set? sometimes you don't want the same elements. 

```python
# define empty set
data = set()
# not data = {} # this is dict
```

### 2.7.2 add

```python
v1 = {1,2,3}
v1.add(4)
print(v1) # {1,2,3,4}
```

### 2.7.3 discard

```python
v1 = {1,2,3}
v1.discard(1)
print(v1) # {2,3}
```

```python
v1 = {1,2,3}
v1.discard(4)
print(v1) # {1,2,3} # no error
```

### 2.7.4 intersection / union /  difference

- intersection

```python
data1 = {'apple', 'banana'}
data2 = {'apple', 'fish'}

# way 1 
result = data1.intersection(data2)
print(result) # 'apple'

# way 2
result = data1 & data2
print(result) # 'apple'
```

- union 

```python
data1 = {'apple', 'banana'}
data2 = {'apple', 'fish'}

# way 1 
result = data1.union(data2)
print(result) # {'apple', 'banana', 'fish'}

# way 2
result = data1 | data2
print(result) # {'apple', 'banana', 'fish'}
```

- difference

```python
data1 = {'apple', 'banana'}
data2 = {'apple', 'fish'}

# way 1 
result = data1.difference(data2)
print(result) # 'banana'

# way 2
result = data1 - data2
print(result) # 'banana'
```

### 2.7.5 public function

- length

```python
data1 = {'apple', 'banana'}
print(len(data1)) # 2
```

- for

```python
data1 = {'apple', 'banana'}
for item in data1:
    print(item)
```

- in

```python
data1 = {'apple', 'banana'}
if 'apple' in data1:
    print('yes')
else:
    print('no')
```

## 2.8 transfer between (list/tuple/set)

```python
data = [1,2,3]
result = tuple(data)
print(result) # (1,2,3)
```

if tuple and list transfer to set:

```python
data = [1,2,2,3]
result = set(data)
print(result) # {1,2,3}
```

## 2.9 None

```python
v1 = None
v2 = ""
```

## 2.10 try and except

bypass error

```python
try: 
    data = input("enter a number: ")
    result = int(data)
    print(result)
except Exception as e:
    print("error")
```

# 3. function

## 3.1 if / elif / else

```python
number = input('enter a number')
data = int(number)

if data > 66:
    print("smaller")
elif data < 66:
    print("bigger")
else:
    print("correct 66")
```

else can skip

- embed

```python
if A > 40:
    if A > 60:
        pass
    else:
        pass
    pass
```

## 3.2 while

```python
while True:
    print('hello')

# infinity loop
```

```python
print('start')

while 1 > 2:
    print('pass')

print('end')

# output 
'start'
'end'
```

- break (only put inside loop)

```python
while True:
    print('pass')
    break
    print('p')

# output 
pass
```

- continue (only put inside loop)

```python
while True:
    print('pass')
    continue
    print('p')

# output 
pass
pass
.. (infinity)
```

## 3.3 operator

```python
value = 2 + 1
print(value) # 3
```

```python
> 
< 
==
!=
>=
<=
```

```python
value = 0
value += 1  # value = value + 1
print(value) # 1
```

```python
+=
-=
```

```python
text = 'hello world'
if 'hello' in text:
    print('yes')
print('no')
```

note: for string ("in" and "not in")

- advance **careful**

```python
v1 = 6 and 9 # 9
v2 = 0 and 1 # 0
v3 = 88 and 0 # 0
v4 = "" and 8 # ""
v5 = 'amy' and 'brian' # 'brian'
v6 = 1 or 2 # 1
v7 = 0 or 2 # 2
```

## 3.4 zip / map

- zip two lists

```python
names = ["Alice", "Bob", "Charlie"]
ages = [25, 30, 35]

zipped = zip(names, ages)
print(list(zipped))  
# [('Alice', 25), ('Bob', 30), ('Charlie', 35)]

########
a = [1, 2, 3]
b = ['a', 'b']

print(list(zip(a, b)))  
# [(1, 'a'), (2, 'b')]
```

- unzipping a list of tuples

```python
zipped_data = [('Alice', 25), ('Bob', 30), ('Charlie', 35)]

names, ages = zip(*zipped_data)
print(names)  # ('Alice', 'Bob', 'Charlie')
print(ages)   # (25, 30, 35)
```

- map: apply a function to every element

```python
numbers = [1, 2, 3, 4]

squared = map(lambda x: x**2, numbers)
print(list(squared))  # [1, 4, 9, 16]
```

# 4. file operation

3 steps for file:

1. open file

2. operation file

3. close file

```python
with open('file path', 'w/r/a') as file: # 'a' is append    
```

## 4.1 write

```python
# open file
file_name = open('xxx.txt', mode='wb')

# write 
name = 'brian'
file_name.write(name.encode('utf-8'))

# close file
file_name.close()
```

Note: using "**wb**": if file not exist, creating a file; if file exist, clean file before write.

## 4.2 append

```python
# open file
file_name = open('xxx.txt', mode='ab')

# write 
name = 'brian'
file_name.write(name.encode('utf-8'))

# close file
file_name.close()
```

Note: using "**ab**": if file not exist, creating a file; if file exist, append new text in the tail. 

## 4.3 read (careful for large data size)

```python
# open file
file_name = open('xxx.txt', mode='rb')

# read 
data = file_name.read()
data_string = data.decode('utf-8')
print(data_string)

# optional split by line
row_list = data_string.strip().split('\n')
print(row_list)

# close file
file_name.close()
```

- important: if file is 100GB

```python
file_name = open('xxx.txt', mode='rb')

# if document is too big, read line by line
for line in file_name:
    line_string = line.decode('utf-8')
    line_string = line_string.strip()
    print(line_string)

file_name.close()
```

## 4.4 with open

```python
with open('xxx.txt', mode='rb') as file_name:
    data = file_name.read()
    print(data)
```

# 5. def

## 5.1 definition

using def to store different functions

```python
PEP 8 name rule: 
calculate()
calculate_math()

##### 
Calculate() # not follow PEP 8
```

```python
def calculate():
    v1 = 2
    v2 = 3
    v3 = v1 + v2
    print(v3)

calculate() # 5
```

```python
def calculate():
    v1 = 2
    v2 = 3
    v3 = v1 + v2
    return v3

data = calculate()
print(data) # 5
```

## 5.2 argument

```python
def xxx(argument_1, argument_2)

xxx(1,2)
```

```python
def calculate(a,b):
    result = a + b
    return result

data = calculate(2,3)
print(data) # 5
```

```python
def calculate(a,b):
    result = a - b
    return result

data = calculate(b=2,a=3)
print(data) # 1
```

```python
def calculate(a,b=1):
    result = a - b
    return result

data = calculate(2)
print(data) # 1
```

```python
def calculate(a,b=1):
    result = a - b
    return result

data = calculate(2,2)
print(data) # 0
```

- *(dynamic parameter 1 star)

argument will change to **tuple**

```python
def func(*a1):
    print(a1)

func(1) # (1,)
func(11,22) # (11,22)
func(11,[22,33]) # (11,[22,33])
```

```python
func([1,2,3]) = only send 1 tuple to def func()
```

- **(dynamic parameter 2 stars) (must use keyword arguments)

argument will change to **dictionary**

```python
def func(**dt):
    print(dt)

func(a1=1,b2=2) # {'a1':1,'b2'"2}
```

- hybrid

```python
def func(*x1, **dt):
    # x1 = (11, 22, 3)    dt = {"xx":123, "uu":999, "b12":"root"}
    # x1 = ()    dt = {}
    print(x1,dt)
    pass

func(11, 22, 3, xx=123, uu=999, b12="root") # (11, 22, 3) {"xx":123, "uu":999, "b12":"root"}
func() # () {}
```

## 5.3 return

```python
def func(a1,a2):
    res = a1 + a2 
    return res

# operate func 
# return the value and store in variable
data = func(100,200)
print(data) # 300
```

```python
def f1():
    return 12
v1 = f1()

######
def f2():
    return [12,22]
v2 = f2()

#####
def f3():
    return (11,22)
v3 = f3()

#####
def f4: 
    return 11,22,33
v4 = f4() # return tuple (11,22,33)
```

- if no return

```python
def f5(a1,a2):
    res = a1 + a2
data = f5() # data = None
```

- if function faces return, function stop operation and return value

```python
def f6():
    print(11)
    print(22)
    return 555 # stop and return 555
    print(33)

res = f6()
# only print 11 and 22. no 33
```

```python
def f7():
    for i in range(10):
        return i

res = f7() # 0
```

- break

```python
def f8():
    for i in range(10):
        break

res = f8() # None
```

- continue

```python
def f9():
    for i in range(10):
        continue

res = f9() # None
```

- if return empty

```python
def f10():
    a = 10 + 1
    return 

res = f10() # None
```

## 5.4 using def

```python
# correct: 
def func():
    print(11)

func()

#########
# incorrect

func1() # error

def func1():
    print(11)
```

```python
def f1():
    print(1)
    print(2)

def f2():
    print(333)
    f1()
    print(444)

f2()
# output
333
1
2
444
```

```python
def f1():
    print(1)
    print(2)

def f2():
    print(333)
    data = f1()
    print(data)
    print(555)

f2()
# output
333
1
2
None
555
```

## 5.5 scope

global and def func():

When looking for the value of a variable, first search within its own scope. If it is not found, then search in the parent scope.

```python
def f1():
    age = 19
    print(age)

def f2():
    print(age)

f1() # 19
f2() # error
```

```python
name = 'brian'

def f3():
    text = "I am "
    data = text + name
    print(data)

f3() # "I am brian""
```

```python
name = 'brian'

def f4():
    text = "I am "
    name = "Joy"
    data = text + name
    print(data)

f4() # 'I am Joy'
```

```textile
self-defined module > Python built-in module > third party module
```

## 5.6 global and local variable

```textile
Global (Upper), local (lower) [PEP 8 rule]
```

- Global variables are declared **outside** a function and can be accessed inside the function unless modified

- Local variables are declared **inside** a function and are only accessible within that function.

```python
# global
NAME = 'brian'

def func():
    # local
    data = 999
```

### 5.6.1 global keyword

```python
NAME = 'brian'

def f1():
    global NAME
    NAME = 'Joy'

print(NAME)
f1()
print(NAME)
# output
'brian'
'Joy'
```

```python
NAME = [11,22]

def f1():
    global NAME
    NAME = [22,33]

print(NAME)
f1()
print(NAME)
# output
[11,22]
[22,33]
```

## 5.7 def name can be variable name

```python
def f1():
    print(11)

f1 = 22
print(f1) # 22
```

```python
def f1():
    print(11)

v1 = f1    # v1 = function f1
v2 = f1()  # v2 = None
v3 = v1()  # v3 = None

# output 
function f1
11
None
11 # v3 = v1() = f1()
None
```

```python
def f1():
    return 111

def f2():
    return 222

data_list = [1, 2, f1, f2, f1(), f2()]

data_list[2] # function f1

data_list[4] # 111

###########
data_dict = {
    '11': f1,
    '22': f2,
}

data_dict.get('22') # function f2

data_dict.get('22')() # 222
```

## 5.8 lambda

note: lambda auto return 

```python
def f1():
    return 123

f2 = lambda : 123

res1 = f1()
res2 = f2()
print(res1, res2) # 123 123
# f1 = f2
```

```python
f3 = lambda a1,a2: a1 + a2
res = f3(1,2)
print(res) # 3
```

```python
f3 = lambda a1: a1.upper()
res = f3('root')
print(res) # ROOT
```

```python
f4 = lambda data: data.append(123)
value = f4([11,22])
print(value) # None
```

## 5.9 python inside function

```python
group 1:
abs, pow, sum, divmod, round
group 2:
min, max, all, any
group 3:
bin, oct, hex,
group 4:
ord, chr
group 5:
int, str, bool, list, dict, set, tuple, float, bytes
group 6:
len, print, input, open, range, hash, type, callable, enumerate, sorted
```

- group 1:

```python
# abs
data = abs(-10)
print(data) # 10

# pow
data = pow(2,5)
print(data) # 2^5 (32)

# sum
data = [1,2]
res = sum(data)
print(res) # 3

# divmod
v1, v2 = divomd(92,10)
print(v1) # 9
print(v2) # 2

# round
data = round(3.14125, 2)
print(data) # 3.14
```

- group 2:

```python
# min
data = [1,2,3]
print(min(data)) # 1

# max
data = [1,2,3]
print(max(data)) # 3

# all: checking all elements are True in bool or not
data = [2, "dd", 88]
res = all(data)
print(res) # True

data = [2, 0, 'dd']
res = all(data)
print(res) # False

# any: checks if at least one element in an iterable is True. If any element is True, it returns True; otherwise, it returns False.
data = [2, 'dd', 0]
res = any(data)
print(res) # True

data = [0, ""]
res = any(data)
print(res) # False
```

- group 3:

```python
# binary
res = bin(100)
print(res) # 0b101001001

# oct 
res = oct(100)
print(res) # 0o1221

# hex
res = hex(100)
print(res) # 0x1221
```

- group 4: (unicode conversion)

```python
# ord
v1 = ord('A')
print(v1) # 65

# chr
v2 = chr(65)
print(v2) # 'A'
```

- group 5: 

```python
int
str
bool
list
dict 
set
tuple
float
bytes
```

- group 6:

```python
len
print
input
open
range
hash
type
callable
enumerate
sorted
```

```python
data = hash('brian')
print(data) # 3285547258501591185 
# get hash value
```

```python
name = 'brian'
print(type(name)) # <class 'str'>
```

```python
# callable: can add () to operate or not
f1 = 3
res = callable(f1)
print(res) # False

def f2(): 
    print(22)
res = callable(f2)
print(res) # True
```

```python
# enumerate 
goods = ['fruits', 'fish', 'cookie']
for index, item in enumerate(goods, 100):
    print(f"{index}: {item}")

# output 
100: fruits
101: fish
102: cookie
```

```python
# sorted
data = [1,3,2]
data.sort()
print(data) # [1,2,3]

#######
data = ['1', '2', '11', '12']
data.sort()
print(data) # ['1', '11', '12', '2']
```

## 5.10 derivation

### 5.10.1 for list

```python
data = [i for i in range(10)]
print(data) # [0,1,2,3,4,5,6,7,8,9]
```

```python
data = [i for i in range(10) if i > 6]
print(data) # [7,8,9]
```

```python
data = [i for i in range(10) if i > 6 and i < 9]
print(data) # [7,8]
```

### 5.10.2 for dict

```python
data = {i:123 for i in range(3)}
print(data) # {0: 123, 1: 123, 2: 123}
```

```python
data = {i:(i,100) for i in range(3)}
print(data) # {0: (0, 100), 1: (1, 100), 2: (2, 100)}
```

```python
data = {i:(i,100) for i in range(3) if i > 1}
print(data) # {2: (2, 100)}
```

# 6. module

- main.py: (Prevents others from executing the program upon import. It can only be executed when run directly)

```python
def run():
    print(123)

if __name__ == '__main__':
    run()
```

## 6.1 import

- import: imports the entire module

```python
import numpy as np
```

- from: imports specific functions, classes, or variables from a module

```python
from math import sqrt
print(sqrt(16))
```

## 6.2 self-define module

**Note:** Make sure not to use the same name as an internal module or an important third-party module.

```python
## common.py file

def f1():
    return 123

## calculate.py file
import common

res = common.f1() # 123
```

```python
## common.py file

def f1():
    return 123

## calculate.py file
from common import f1
res = f1() # 123
```

## 6.3 python inside module

### 6.3.1 hashlib(md5)

```textile
security
```

```python
import hashlib

data = 'admin'

obj = hashlib.md5()
obj.update(data.encode('utf-8'))
res = obj.hexdigest()
print(res) # 21232f297a57a5a743894a0e4a801fc3
```

```python
# add salt
import hashlib

data = 'admin'

salt = 'dfeoneweoren' # write what you like
obj = hashlib.md5(salt.encode('utf-8'))
obj.update(data.encode('utf-8'))
res = obj.hexdigest()
print(res) # 8566e6191fd48e52d950004fe0f46d82
```

### 6.3.2 random

random select 

```python
import random
v1 = random.randint(1,20) # 1 <= v1 <= 20
print(v1) # 2
```

### 6.3.3 json

```python
res = json.dumps(info) # python to json format
res = json.loads(info) # json to python format

for other language in the dictionary 
res = json.dumps(info, ensure_ascii=False)
```

Note: 

- The outer structure is a complete string.

- If a JSON string contains a string inside, it must use **double quotes**.

- JSON strings **do not support** tuple formats like those in Python.

```python
v1 = '{ "k1": 123, "k2": 456 }'
v2 = "{'k1': 123, 'k2': 456}"
v3 = '{ "k1": 123, "k2": 456, "k3": [11, 22, 33] }'
v4 = '{ "k1": 123, "k2": 456, "k3": (11, 22, 33) }'

########
v1 and v3 is JSON
v2 and v4 is NOT JSON

########
v2 => Uses single quotes ' for keys, should be "
v4 => Uses a tuple (), which is not valid in JSON
```

```python
import json

info = { "k1": 123, "k2": 456, "k3": (11, 22, 33) }
res = json.dumps(info)
print(res) # {"k1": 123, "k2": 456, "k3": [11, 22, 33]}
```

```python
import json 
info = '{"k1": 123, "k2": 456, "k3": [11, 22, 33]}''
res = json.loads(info)
print(res) # {'k1': 123, 'k2': 456, 'k3': [11, 22, 33]}
```

```python
# other language 
import json

info = {"k1": "中文", "k2": 456, "k3": [11, 22, 33]}
res = json.dumps(info, ensure_ascii=False)
print(res) # '{"k1": "中文", "k2": 456, "k3": [11, 22, 33]}''
```

- Serialization

In Python, only basic data types can be serialized using the `json` module by default.

```python
+------------+--------+
| Python     | JSON   |
+------------+--------+
| dict       | object |
| list, tuple | array  |
| str        | string |
| int, float | number |
| True       | true   |
| False      | false  |
| None       | null   |
+------------+--------+
```

```python
# example:
import json
import requests

# Set the URL for the request
url = "https://movie.douban.com/j/search_subjects?type=movie&tag=%E7%83%AD%E9%97%A8&sort=recommend&page_limit=20&page_start=20"

# Set the headers with a user agent
headers = {
    "user-agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/95.0.4638.69 Safari/537.36"
}

# Send a GET request to the URL
res = requests.get(url, headers=headers)

# Load the JSON response into a dictionary
data_dict = json.loads(res.text)

# Iterate through the 'subjects' in the data dictionary
for item in data_dict['subjects']:
    # Print the title and URL of each item
    print(item['title'], item['url'])
```

```python
# example: 
import json
from flask import Flask

app = Flask(__name__)

@app.route('/get/info')
def index():
    data = {'歡迎', '您好', '世界'}
    json_string = json.dumps(list(data), ensure_ascii=False)  # Ensure ASCII is False to preserve non-ASCII characters
    return json_string

@app.route('/do/play')
def play():
    info = {
        'code': 1000,
        'status': True,
        'values': [
            {'id': 1, 'name': '歐洲'},
            {'id': 2, 'name': '亞洲'},
            {'id': 3, 'name': '美洲'}
        ]
    }
    json_string = json.dumps(info, ensure_ascii=False)  # Ensure ASCII is False to preserve non-ASCII characters
    return json_string

if __name__ == '__main__':
    app.run()
```

### 6.3.4 time

```python
import time

v1 = time.time() # get current time (from 1970/1/1)
print(v1) # 1740267988.1394591
```

### 6.3.5 datetime

```python
import datetime

v1 = datetime.datetime.now()
print(v1) # 2025-02-22 15:48:14.942253
```

```python
import datetime

v1 = datetime.datetime.now().strftime("%Y-%m-%d" %H:%M:%S)
print(v1) # 2025-02-22 15:49:36 (string format)
```

- string to datetime

```python
from datetime import datetime

text = "2021-11-11"
res = datetime.strptime(text, "%Y-%m-%d")
print(res, type(res))
```

- datetime to string

```python
from datetime import datetime

dt = datetime.now()
res = dt.strftime("%Y-%m-%d-%H-%M")
print(res)
```

- time to datetime

```python
import time
from datetime import datetime

ctime = time.time()

dt = datetime.fromtimestamp(ctime)
print(dt, type(dt))
```

- datetime to time

```python
from datetime import datetime

v1 = datetime.now()
res = v1.timestamp()
print(res)
```

### 6.3.6 os

```python
path / file(delete) / folder(create/exist/list)
```

- path connection

```python
import os
path = os.path.join('x1','x2','log.txt')
print(path) # x1/x2/log.txt
```

- find parent directory

```python
import os

file_path = "x1/x2/x3/x4"

# Find the parent directory of the current path
v1 = os.path.dirname(file_path)
print(v1)  # Output: x1/x2/x3
```

- abs path

```python
import os

res = os.path.abspath('xx')
```

- path exist or not

```python
import os

file_path = "xxx/xxx/ss/xx.png"

res = os.path.exists(file_path)
print(res) # True or False
```

- create folder

```python
import os 

path = os.path.join('db', '2021', '11 month')

if not os.path.exists(path):
    os.makedirs(path)
```

- delete file / delete folder

```python
import os 

path = os.path.join('db', '2021', '11 month', 'log.txt')

# delete file
os.remove(path)
```

```python
import os 
import shutil

path = os.path.join('db', '2021')

# delete folder
shutil.rmtree(path)
```

- folder is exist or not

```python
import os

path = os.path.join('db', '2021')
res = os.path.isdir(path)
print(res)
```

### 6.3.7 shutil

```python
file(copy) / folder(delete/copy/rename) / zip
```

- delete folder

```python
import shutil

shutil.rmtree('xxx/xx/xx/xxx')
```

- copy folder

```python
shutil.copytree('original_folder', 'original_folder_path')
```

- copy file

```python
import shutil

# Copy a single file to a directory (ensure the directory exists)
shutil.copy("source_file.txt", "destination_folder/")
```

- re-name

```python
import shutil

# file re-name
shutil.move('x10', 'x10.txt')

# folder re-name
shutil.move('x1','x100')
```

- zip

```python
import shutil

# base_name: Name of the output archive (without extension)
# format: Compression format ('zip', 'tar', 'gztar', etc.)
# root_dir: Directory to be compressed

shutil.make_archive(base_name='1116', format='zip', root_dir="ppp")
# This creates a 1116.zip file containing everything from the ppp folder.
```

```python
# filename: The archive file to extract
# extract_dir: The destination folder for extracted files
# format: The compression format

shutil.unpack_archive(filename="1116.zip", extract_dir="1117", format='zip')
# This extracts the 1116.zip archive into the 1117 folder.
```

### 6.3.8 re

```python
re.findall()
re.match()
re.search()
re.split()
```

#### re.findall()

**`re.findall`**: Retrieves all successful matches.

- string-related operations

```python
import re

text = "hello wupeiqi, i am wupeiqasd, your brother is wupeiqiff"

data_list = re.findall("wupeiqi", text)
print(data_list)  # ["wupeiqi", "wupeiqi"]
```

- matching specific characters

```python
import re

text = "hello wupeiqi, i am wupeiqasd, your brother is wupeiqiff"
data_list = re.findall("[abc]", text)
print(data_list)  # ['a', 'a', 'b']
```

- character ranges (a-z, 0-9)

```python
import re

text = "alexrootrootadmin"
data_list = re.findall("t[a-z]", text)
print(data_list)  # ['tr', 'ta']
```

- \d: represents a single **digit** 

```python
import re

text = "root-ad32min-add3-admlin"
data_list = re.findall(r"d\d", text)
print(data_list)  # ['d3', 'd3']
```

```python
import re

text = "root-ad32min-add33322-admlin"
data_list = re.findall(r"d\d+", text)  # `+` means 1 or more occurrences
print(data_list)  # ['d32', 'd33322']
```

```python
import re

text = "root-ad32min-add33322-admlin"
data_list = re.findall(r"d\d*", text)  # `*` means 0 or more occurrences
print(data_list)  # ['d', 'd32', 'd33322', 'd']
```

```python
import re

text = "rodot-ad32min-add33322-admlin"
data_list = re.findall(r"d\d?", text)  # `?` means 0 or 1 occurrence
print(data_list)  # ['d', 'd3', 'd', 'd3', 'd']
```

```python
import re

text = "rodot-ad32min-add33322-admlin"
data_list = re.findall(r"d\d{2}", text)  # `{2}` means exactly 2 digits
print(data_list)  # ["d32", "d33"]
```

```python
import re

text = "rodot-ad32min-add33322-admlin"
data_list = re.findall(r"d\d{2,}", text)  # `{2,}` means 2 or more digits
print(data_list)  # ["d32", "d33322"]
```

```python
import re

text = "rodot-ad32min-add33322-admlin"
data_list = re.findall(r"d\d{2,4}", text)  # `{2,4}` means 2 to 4 digits
print(data_list)  # ['d32', 'd3332']
```

- \w: Letters, Numbers, Underscores (Word Characters)

```python
import re

text = "hello, where are you?"

data_list = re.findall(r'h\w+o', text) 
print(data_list)  # ['hello']
```

```python
import re

text = "hellowhereareyou?"

data_list = re.findall(r'h\w+e', text) # Greedy match (default)
print(data_list)  # ['hellowhereare']
```

```python
import re

text = "hellowhereareyou?"

data_list = re.findall(r'h\w+?e', text) # Non-greedy match (default)
print(data_list)  # ['hellowhe'] 
```

- . : Match Any Character Except Newline

```python
import re

text = "alexraotrootadmin"
data_list = re.findall(r"r.o", text)  
print(data_list)  # ['rao', 'roo']
```

```python
import re

text = "alexraotrootadmin"
data_list = re.findall(r"r.+o", text)  # greedy
print(data_list)  # ['raotroo']
```

```python
import re

text = "alexraotrootadmin"
data_list = re.findall(r"r.+?o", text)  # greedy
print(data_list)  # ['rao', 'roo']
```

- \s: Represents Any Whitespace Character

```python
import re

text = "root admin fdd dmin"
data_list = re.findall(r"a\w+\s\w+", text)
print(data_list)  # ['admin fdd']
```

##### Quantifiers

- `*` → **0 or more**
- `+` → **1 or more**
- `?` → **0 or 1**
- `{n}` → **Exactly n times**
- `{n,}` → **At least n times**
- `{n,m}` → **Between n and m times**

**Note:**

- **Greedy matching is the default behavior.**

- **To make it non-greedy, use `?` after the quantifier (e.g., `+?`).**

---

- extract range

```python
import re

text = 'number 112234345 and number 112285984'
data = re.findall(r'1122\d{5}', text)
print(data) # ['112234345', '112285984']
```

```python
import re

text = 'number 112234345 and number 113385984'
data = re.findall(r'1122\d{5} | 1133\d{5}', text)
print(data) # ['112234345 ', ' 113385984']
```

#### re.match()

**`re.match`**: Tries to match from the beginning of the string. If the start does not match, it does not check further and returns only the first match object.

```python
import re

text = "hello world, hello Python"

# Using re.findall - Finds all occurrences
all_matches = re.findall(r"hello", text)
print("findall result:", all_matches)  # ['hello', 'hello']

# Using re.match - Only checks at the start
match_result = re.match(r"hello", text)
print("match result:", match_result.group() if match_result else "No match")  # 'hello'

# Using re.match with a different word that doesn't start the string
match_result_fail = re.match(r"world", text)
print("match result (world):", match_result_fail.group() if match_result_fail else "No match")  # 'No match'
```

#### re.search()

`re.match` : **Finds the first occurrence of a pattern** anywhere in the string.

```python
import re

text = "Python is amazing. I love Python!"

# Search for 'Python' in the text
match = re.search(r"Python", text)

if match:
    print("Found:", match.group())  # Output: 'Python'
    print("Position:", match.start(), "to", match.end())  # Output: '0 to 6'
else:
    print("Not found")
```

#### re.split()

`re.split()` : **Splits the string** at each match of the pattern.

```python
import re

text = "apple, banana; orange|grape"

# Split using multiple delimiters (comma, semicolon, and pipe)
split_result = re.split(r"[,;|]", text)

print(split_result)  # Output: ['apple', ' banana', ' orange', 'grape']
```

# 7. class

```python
class ClassName:
    def f1():
        xxx
    def f2():
        yyy
    def f3():
        zzz
```

PEP 8 Rule:

- Class names should follow the **CapWords (PascalCase)** convention.

- Do **not** use underscores or lowercase letters.

If we implement the following code using an object-oriented approach:

- **Define classes and methods**
- **Call methods inside a class**
  - Instantiate an object from the class
  - Call methods using the object

```python
# Class name (Capitalized)
class Message:

    # Define a method inside the class: send_email
    def send_email(self, to_email):
        msg = "{} has received an email".format(to_email)
        print(msg)

obj = Message()  # Creating an instance of the Message class
obj.send_email("424662508@gmail.com") # 424662508@gmail.com has received an email
```

- example 1:

```python
class Message:

    def send_email(self, to_email):
        msg = "{} has received an email.".format(to_email)
        print(msg)

    def send_dingding(self, to_email):
        msg = "{} has received a DingTalk message.".format(to_email)
        print(msg)

    def send_wechat(self, to_email):
        msg = "{} has received a WeChat message.".format(to_email)
        print(msg)


# Instantiate the Message object
# 1. Allows storing other objects
# 2. Can save data for reuse

obj = Message()

obj.send_email("x1")
obj.send_dingding("x2")
obj.send_wechat("Zhang San") 
"""
x1 has received an email.
x2 has received a DingTalk message.
Zhang San has received a WeChat message.
"""
```

- example 2: 

```python
class Message:

    def send_email(self, to_email):
        msg = "{} has received an email.".format(to_email)
        print(msg)

    def send_dingding(self, to_email):
        msg = "{} has received a DingTalk message.".format(to_email)
        print(msg)

    def send_wechat(self, to_email):
        msg = "{} has received a WeChat message.".format(to_email)
        print(msg)


# Instantiate the Message object
obj = Message()

# Assign attributes to the object
obj.company = "China Unicom"
obj.number = 10000

# Print the assigned attributes
print(obj.company)  # Output: "China Unicom"
print(obj.number)   # Output: 10000
```

- example 3: 

```python
class Message:

    def send_email(self, to):
        msg = "{} has sent an email to {}.".format(self.company, to)
        print(msg)

    def send_dingding(self, to):
        msg = "{} has received a DingTalk message.".format(to)
        print(msg)

    def send_wechat(self, to):
        msg = "{} has received a WeChat message.".format(to)
        print(msg)


# Instantiate the Message object
obj = Message()

# Assign attributes to the object
obj.company = "China Unicom"
obj.number = 10000

# Print the assigned attributes (commented out in the original code)
# print(obj.company)  # "China Unicom"
# print(obj.number)   # 10000

# Call the send_email method
obj.send_email("Wang Xiaomei")  # "China Unicom has sent an email to Wang Xiaomei."
```

- example 4: 

```python
class Message:
    # Special method, automatically called by Python when an instance is created.
    # The __init__ method is executed immediately after instantiation.
    def __init__(self, city):
        self.company = "China Unicom"
        self.city = city

    def send_email(self, to):
        msg = "{} ({}) has sent an email to {}.".format(self.company, self.city, to)
        print(msg)

    def send_dingding(self, to):
        msg = "{} ({}) has sent a DingTalk message to {}.".format(self.company, self.city, to)
        print(msg)

    def send_wechat(self, to):
        msg = "{} ({}) has sent a WeChat message to {}.".format(self.company, self.city, to)
        print(msg)


# 1. Create objects and establish attribute relationships
# 2. __init__ is automatically called upon instantiation

obj1 = Message("Guangdong")  # obj1.__init__("Guangdong")
obj2 = Message("Henan")      # obj2.__init__("Henan")

obj1.send_email("Zhang San")
obj1.send_email("Li Si")
obj2.send_email("Wang Wu")
"""
China Unicom (Guangdong) has sent an email to Zhang San.
China Unicom (Guangdong) has sent an email to Li Si.
China Unicom (Henan) has sent an email to Wang Wu.
"""
```

- police game example: 

```python
class Police:
    """ Police Class """

    def __init__(self, name, age, hit_points):
        self.name = name
        self.age = age
        self.hit_points = hit_points

    def catch(self):
        """ Catching a thief """
        self.hit_points = self.hit_points + 100
        print(self.hit_points)

    def smoking(self):
        """ Smoking """
        self.hit_points = self.hit_points - 50
        print(self.hit_points)

    def shoot(self, user):
        """ Shooting """
        user.hit_points = user.hit_points - 100
        self.hit_points = self.hit_points - 10
        print(self.hit_points, user.hit_points)


# Creating Police objects
p1 = Police("Li Guomin", 22, 1000)
p2 = Police("Chen Chao", 22, 200)
p3 = Police("Deng Xincheng", 22, 8000)


p1.catch() # p1 from 1000 to 1100
p2.smoking() # p2 from 200 to 150
p3.shoot(p1) # p3 from 8000 to 7990 / p1 from 1100 to 1000
p2.shoot(p3) # p2 from 150 to 140 / p3 from 7990 to 7890
p1.shoot(p2) # p1 from 1000 to 990 / p2 from 140 to 40
"""
1100
150
7990 1000
140 7890
990 40
"""
```

## 7.3 big 3 features

### 7.3.1 Encapsulation

Encapsulating data into objects

```python
class UserInfo:
    def __init__(self, name, age, email):
        self.name = name
        self.age = age
        self.email = email


obj1 = UserInfo("Wu Peiqi", 99, "xx@live.com")
obj2 = UserInfo("Wu Peiqi", 99, "xx@live.com")
obj3 = UserInfo("Wu Peiqi", 99, "xx@live.com")
obj4 = UserInfo("Wu Peiqi", 99, "xx@live.com")
obj5 = UserInfo("Wu Peiqi", 99, "xx@live.com")
```

- same types classify: categorizing functions of the same type into a class

```python
class Message:
    """ Message Sending Class """

    def email(self):
        pass

    def wechat(self):
        pass

    def dingding(self):
        pass


class FileHandler:
    """ File Operations Class """

    def txt(self):
        pass

    def excel(self):
        pass

    def word(self):
        pass
```

### 7.3.2 inheritance

put same def() to the "class Base" from "class F1" and "class F2"

class Base calls "**superclass**" and class F1 and F2 call "**subclass**"

```python
## single inheritance:
class Foo:
    pass

# Subclass inheriting from parent class
class Son(Foo):
    pass
```

```python
## multi-level inheritance
class Base:
    def show(self):
        print("123")

class F1(Base):
    def do(self):
        pass

class F2(Base):
    def exec(self):
        pass
```

```python
class F1:
    pass

class F2:
    pass

class Foo(F1, F2):
    pass

obj = Foo()
obj.xxx()  # Example call
```

- **First, it checks in `Foo` itself.**
- **If not found, it searches in the leftmost parent (`F1`).**
- **If still not found, it searches in the right parent (`F2`).**

example:

```python
class Base:
    def do(self):
        print("base.do")

class Son(Base):
    def do(self):
        print("do")

    def show(self):
        print("show")
        self.do()

sl = Son()
sl.show()

# Output:
# show
# do
```

```python
class Base:
    def do(self):
        print("base.do")

    def show(self):
        print("show")
        self.do()  # Equivalent to sl.do()

class Son(Base):
    def do(self):
        print("do")

sl = Son()
sl.show()

# Output:
# >>> show
# >>> do
```

```python
class TCPServer:
    def f1(self):
        print("TCPServer")

class ThreadingMixIn:
    def f1(self):
        print("ThreadingMixIn")

class ThreadingTCPServer(ThreadingMixIn, TCPServer):
    def run(self):
        print('before')
        self.f1()  # obj.f1()
        print('after')

obj = ThreadingTCPServer()
obj.run()

# Output:
# >>> before
# >>> ThreadingMixIn
# >>> after
```

### 7.3.3 polymorphism

In Java and other programming languages, **polymorphism** is a fundamental concept.

Python **natively supports polymorphism**, meaning functions and methods can operate on **multiple types**.

```python
# The 'arg' parameter can take multiple forms (various types of objects)
def func(arg):
    arg.send()

# For the func function, 'arg' can be any type of object
# As long as the object has a 'send' method, it will work

class F1:
    def send(self):
        pass

class F2:
    def send(self):
        pass

obj1 = F1()
obj2 = F2()

func(obj1)  # Works because obj1 has a 'send' method
func(obj2)  # Works because obj2 also has a 'send' method
```

**Explanation:**

1. **`func(arg)`** is a generic function that calls `arg.send()`, but it **does not care about the object's type**.
2. **Both `F1` and `F2`** define a `send()` method.
3. The function `func()` successfully operates on **both objects (`obj1` and `obj2`)**.
4. **This is polymorphism:** A function or method can handle **multiple types of objects** as long as they follow a common interface (`send()` in this case).
