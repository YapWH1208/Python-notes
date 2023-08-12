- `__iter__`函数是一个可以将可迭代数据类型可迭代化的函数
- 通常情况会伴随`__next__`函数一同使用作为遍历数据的函数

## 例子
```py
class MyIterable:
    def __init__(self, data):
        self.data = data
        self.index = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.index >= len(self.data):
            raise StopIteration
        item = self.data[self.index]
        self.index += 1
        return item

my_list = MyIterable([1, 2, 3, 4, 5])

for item in my_list:
    print(item)
```

### 输出
```py
1 
2 
3 
4 
5
```

# 问题
## 1. 如何知道哪些数据类型可迭代？
```py
from collections import abc

print(isinstance([],abc.Iterable))
print(isinstance([],abc.Iterator))
```

输出：
```py
True 
False
```

### 解：
- `[]`为一个可迭代数据类型，但非一个迭代器。
<br>
## 2. 什么是可迭代数据类型和迭代器
- 简而言之，可迭代数据类型具备转换成迭代器的能力。
- 可迭代数据类型只需使用`iter()`函数即可转换成迭代器
- 而迭代器是拥有被遍历数据的能力
```py
# [1,2,3]为可迭代数据类型但非迭代器
# iter([1,2,3])为迭代器

for i in [1,2,3]:
	print(i)
```

输出：
```
1
2
3
```

- 为什么`[1,2,3]`为非迭代器可以被遍历呢？
### 解：
- 从python的底层逻辑上说，但凡被传入的遍历对象是个可迭代数据类型就会自动使用`iter()`

## 3. 为什么要同时拥有可迭代数据类型和迭代器
```py
f = open('data.txt')
for i in f:
	pass
print(f.read())

lt = [1,2,3]
for i in lt:
	pass
print(lt)
```

输出：
```py

[1,2,3]
```

### 解：
- 迭代器拥有状态。当一个迭代器遍历完毕后仍然保持状态。从例子上讲解为当文本遍历完毕后，指针会依旧指向文本末位+1的位置。
- 可迭代数据类型不存状态。无论遍历完毕与否都可以重新访问/遍历

# 附
## `__iter__`的特殊特性
```py
def fun(): 
	import random 
	return random.randint(1,6) 

for i in iter(fun ,5): 
	print(i)
```
输出:
```
1
4
4
```

### 解：
- 这个是一个抽奖代码，当`iter()`中的哨兵值未被满足是会不断的递归函数