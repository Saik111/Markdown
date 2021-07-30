Python基础



## 变量和简单数据类型



#### 修改字符串的大小写的方法



1. `title()` 将每个单词的首字母都大写

2. `upper()` 将字符串改为全部大写

3. `lower()` 将字符串改为全部小写



==演示代码3-1==

```python
name = "ada lovelace"

print(name.title())

print(name.upper())

print(name.lower())
```

==运行结果==

```python
Ada Lovelace

ADA LOVELACE

ada lovelace
```



#### 使用制表符或换行符来添加空白



1. `\t` 在字符串中添加制表符

2. `\n` 在字符串中添加换行符



==代码演示2-1==

```python
"""

字符串"\n\t"

让Python换一行

并在下一行开头添加一个制表符

"""

print("Languages:\n\tPython\n\tC\n\tJavaScript")
```

==运行结果==

``` python
Languages:

	Python

    C

    JavaScript
```



#### 删除空白



1. `rstrip()` 删除字符串末尾的空白

2. `lstrip()` 删除字符串开头的空白

3. `strip()`  删除字符串两边的空白



==演示代码3-1==

```python
favorite_language = ' python '


print(favorite_language.rstrip())

print(favorite_language.lstrip())

print(favorite_language.strip())
```

==运行结果==

```python
' python'

'python '

'python'
```



---



## 列表介绍

####  **`[]`**表示列表，并用逗号分隔其中的元素，索引从0而不是1开始



==演示代码1-1==

```python
bicycles = ['trek', 'cannondale', 'redline', 'specialized']


print(bicycles)

print(bicycles[0])

print(bicycles[0].title())
```

==运行结果==

```python
['trek', 'cannondale', 'redline', 'specialized']

trek

Trek
```



#### 修改、添加和删除元素



1. `lst.append(val)` 在列表尾部添加元素



==演示代码 2-1==

```Python
motorcycles = ['honda', 'yamahe', 'suzuki']

motorcycles.append('ducati') # 方法append()将元素'ducati'添加到

# 列表末尾，而不影响列表中的其他所有元素

print(motorcycles)
```

==运行结果==

```python
['honda', 'yamahe', 'suzuki', 'ducati']
```



2. `lst.insert(idx,  val)` 在列表的任何位置添加新元素



==演示代码 2-3==

```Python
motorcycles = ['honda', 'yamahe', 'suzuki']

motorcycles.insert(0, 'ducati') # 方法insert()在索引0处添加空间，

\# 并将值'ducati'存储到这个地方

print(motorcycles)
```

==运行结果==

```python
['ducati', 'honda', 'yamahe', 'suzuki']
```



3. `del lst[idx]` 知道要删除元素在列表中位置，并删除

   

==演示代码 2-3==

```Python
motorcycles = ['honda', 'yamahe', 'suzuki']

del motorcycles[0] # 使用del可删除了列表motorcycles中第一个元素

\# honda,条件是知道其索引

print(motorcycles)
```

==运行结果==

```python
['yamahe', 'suzuki']
```



4. `lst.pop([idx])` 删除并返回索引idx（默认为结尾）的元素，并接着使用它



==演示代码 2-4==

```Python
motorcycles = ['honda', 'yamahe', 'suzuki']

popped_motorcycles.pop() # 列表末尾的值'suzuki'已删除，它现在

# 被赋给了变量popped_motorcycles

print(motorcycles)

print(popped_motorcycles)
```

==运行结果==

```python
['honda', 'yamahe']

suzuki
```



5. `lst.remove(val)` 找到val在该列表的位置，并删除



==演示代码 2-5==

```Python
motorcycles = ['honda', 'yamahe', 'suzuki', 'ducati']

too_expensive = 'ducati'

motorcycles.remove(too_expensive) # 用remove()删掉列表中被定义为too_expensive的值，并指出删除原因

print(motorcycles)

print(f"\nA {too_expensive.title()} is too expensive for me.")
```

==运行结果==

```python
['honda', 'yamahe', 'suzuki']

A Ducati is too expensive for me.
```



#### 组织列表



1. `lst.sort()` 永久性地修改列表元素的排列顺序

2. `lst.reverse()` 倒着打印列表

3. `len(c)` 可快速获悉列表的长度



==演示代码 3-1==

```python
cars = ['bmw', 'audi', 'toyota', 'subaru']

cars.sort() # 或者用print(sorted(cars))也可以达到同样的输出结果

print(cars)
```

==运行结果==

```python
['audi', 'bmw', 'subaru', 'toyota']
```



---



## 操作列表



####  **`for`**循环，遍历整个列表，对列表中的每个元素都执行相同的操作



* 小心：
  * 忘记缩进额外的代码行和不必要的缩进
  * 循环后不必要的缩进
  * 漏掉冒号



#### 创建数值列表



1. `range([start,]end[,step])` 生成系列数，或创建数字列表

2. `min(c) max(c) sum(c)` 对数字列表执行简单的统计计算

3. ==列表解析== 将`for`循环和创建新元素的代码合并成一行，并自动附加新元素

   

`range(1, 5)` $\rightarrow$​ ​`   1 2 3 4`

`range(2, 12, 3)` $\rightarrow$ `2 5 8 11`



==代码演示2-1==

```python
squares = [] # 创建一个名为squares的空列表



for value in range(1, 11):

	squares.append(value**2)

print(squares)

squares = [value**2 for value in range(1, 11)]
```

==运行结果==

```python
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```



#### 使用列表的一部分



1. ==切片== 和`range()`同理，在到达第二个索引之前的元素后停止

2. ==遍历切片== 如果要遍历列表的部分元素，可在`for`循环中使用切片

3. ==复制列表== 根据既有列表创建全新的列表



==代码演示3-1==

```python
players = ['charles', 'martina', 'michael', 'florence', 'eli']

print("Here are the first three players on my teams:")

for player in players[0:3]:

    print(player.title())
```

==运行结果==

```python
Here are the first three players on my teams:

Charles

Marina

Michael
```



#### 元祖（不可变的列表）



1. ==元祖== 元祖看起来很像列表，但使用圆括号而非方括号来标识

2. ==遍历元祖== 用`for`循环来遍历

3. ==修改元祖变量== 虽然不能修改元祖的元素，但可以给存储元祖的变量赋值



```python
dimensions = (200, 50) # 元祖

for dimensions in dimensions: # 遍历元祖
```



---



## 字典



#### 使用字典



* 键与键之间用冒号分隔，而键值对之间用逗号分隔



1. 访问字典中的值



==演示代码1-1==

```python
aline_0 = {'color': 'green', 'points': 5}

print(aline_0['color'])
```

==运行结果==

```python


green
```



2. 添加（或创建）键值对

   

==演示代码1-2==

```python
aline_0 = {'color': 'green', 'points': 5}

alien_0['x_position'] = 0

alien_0['y_position'] = 25

print(alien_0)
```

==运行结果==

```python
{'color': 'green', 'points': 5, 'x_position': 0, 'y_position': 25}
```



3. 修改字典中的值



==演示代码1-3==

```python
alien_0 = {'color': 'green'}

aline_0['color'] = 'yellow'

print(f"The alien is now {alien_0['color']}.")
```

==运行结果==

```python
The alien is now yellow.
```



4. 删除键对（注：删除的键对会永久消失）



==演示代码1-4==

```python
alien_0 = {'color' = 'green', 'point': '5'}

del alien_0['points']


print(alien_0)
```

==运行结果==

```python
{'color': 'green'}
```



5. 使用`get()`来访问值



==演示代码1-5==

```python
alien_0 = {'color' = 'green', 'speed': 'slow'}

point_value = alien_0.get('point', 'No point value assigned')

print(point_value)
```

==运行结果==

```python
No point value assigned
```



#### 遍历字典



1. `for` 循环遍历所有键对值

2. 遍历字典中的所有键/值



==演示代码2-1==

```python
user_0 = {

    'username': 'efermi',

    'first': 'enrico',

    'last': 'fermi',
}

for key, value in user_0.items(): # 使用这两个变量来打印每个建

# 及其相关联的值

    print(f"Key: {key}")

    print(f"Value: {value}")
```

==运行结果==

```python
Key: username

Value: efermi

Key: first

Value: enrico

Key: last

Value: fermi
```



---



## 用户输入和`while`循环



#### 函数`input()`的工作原理



1. `input()` 让程序暂停运行，等待用户输入一些文本

2. `int()` 获取数值输入

3. 求模运算符`%`,它将两个数相除并返回余数



==演示代码1-1==

```python
height = input("How tall are you, in inches?")

height = int(height)


if height >= 48:

    print("\nYou're tall enough to ride!")

else:

    print("\nYou'll be able to ride when you're a little older")
```

==运行结果==

```python
How tall are you, in inches? 20

You'll be able to ride when you're a little older
```



#### 使用`while`循环



`for` 循环用于针对集合中的每个元素都执行一个代码块，而`while`循环则不断运行，直到指定条件不满足为止



==演示代码2-1==

```python
current_number = 1

while current_number <= 5:

    print(current_number)

    current_number += 1 
```

==运行结果==

```python
1

2

3

4

5
```



---



## 类



#### 方法`__init__()`



方法`__init__()`是一个特殊方法，每当你根据`Dog`类创建新的实例时，Python都会自动运行它。在这个方法的名称中，开头和末尾各有两个下划线，这是一种约定，旨在避免Python默认方法与普通方法发生名称冲突。务必确保`__init__()`的两边都有两个下划线，否则当你使用类来创建实例时，将不会自动调用这个方法，进而引发难以发现的错误



==演示代码1-1==

```python
# 创建一个表示小狗的类 Dog

# 包含名字和年龄 + 蹲下和打滑

# 使用类去创建表示特定小狗的实参Dog()传递名字和年龄，self会自动传递

class Dog():

    """一次模拟小狗的简单尝试"""
    
    
    def __init__(self, name, age):

        """初始化属性 name 和 age"""

        # 以self为前缀的遍历都可供类中的所有方法使用

        # 获取存储在形参name中的值，并将其存储到变量name中，然后

        # 该变量被关联到当前创建的实例

        self.name = name

        self.age = age


    def sit(self):

        """模拟小狗收到命令时蹲下。"""

        print(f"{self.name} is now sitting.")

    
    def roll_over(self):

        """模拟小狗收到命令时打滚。"""

        print(f"{self.name} rolled over!")

        
my_dog = Dog('Willie', 6)

print(f"My dog's name is {my_dog.name}.")

print(f"My dog is {my_dog.age} years old.")
```

==运行结果==

```python
My dog's name is Willie.

My dog is 6 years old
```



---



# 函数



#### 函数定义



函数是带名字的代码块，用于完成具体任务，使用关键字`def`来定义



==演示代码1-1==

```python
def green_user(user_name):

    """显示简单的问候语。"""

    print(f"Hello!{user_name.title()}")

    
greet_user("nana")
```

==运行结果==

```python
Hello!Nana
```



#### 函数调用



需要在程序中多次执行同一项任务时，无需反复编写完成该任务的代码，只需要调用执行该任务的函数，让Python运行其中的代码即可。



==演示代码2-1==

```python
def describe_pet(animal_type, pet_name):

    """显示宠物的信息。"""

    print(f"\nI have a {animal_type}.")

    print(f"My {animal_type}'s name is {pet_name.title()}")


describe_pet('hamster', 'harry')

describe_pet('dog', 'willie')
```

==运行结果==

```python
I have a hamster.

My hamster's name is Harry


I have a dog.

My dog's name is Willie
```

