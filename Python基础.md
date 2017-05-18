# Python基础

## 变量和简单的数据类型

- ### 变量

  - ```python
    # 用变量存储字符串,再打印这个变量.
    message = "Hello Python world!"
    print(message)
    ```

  - ```python
    message = "Hello Python world!"
    print(message)
    message = "Hello Python Crash Course world!"
    print(message)
    # Hello Python world!
    # Hello Python Crash Course world!
    # 变量赋值会覆盖之前的.在程序中可随时修改变量的值，而Python将始终记录变量的最新值
    ```

- ### 字符串

  -    字符串可以用单引号,可以用双引号.
  -    title()方法: 以首字母大写的方式显示每个单词.
  -    upper()方法: 全部改为大写字母.
  -    lower()方法: 全部改为小写字母.


## 列表

## if条件判断

- == 比较字符串,会比较大小写.

- and和or关键字 and相当于js的&&;or相当于js的||

- in关键字, 判断值是否在列表中

- not in 关键字,判断是否不包含在列表中

- 布尔表达式 True False ; 与js不同,是大写哦^_^

- 靠缩进表达if需要执行内容

- else代码块可以省略

- if-elif-else结构

  - ```python
    age = 12
    if age < 4:
    	print("Your admission cost is $0.")
    elif age < 18:
    	print("Your admission cost is $5.")
    else:
    	print("Your admission cost is $10.")
    ```

  - if-系列只会执行一次,如果需要运行多个代码块,就使用一系列独立的if语句.

- 空列表[]代表False,有至少一个元素的列表True

## 字典

- 就是js的对象{}

- 字典内部的顺序无所谓

- ```python
  # 获取字典的值 和js不同的是用[]获取
  alien_0 = {'color': 'green'}
  print(alien_0['color'])

  #添加键-值对 和js不同的是[]直接出来  
  alien_0 = {'color': 'green'}
  alien_0['points'] = 5
  print(alien_0['points'])

  # 创建空字典  类似js创建对象字面量

  # 修改字典中的值
  alien_0 = {'color': 'green'}
  print("The alien is " + alien_0['color'] + ".")
  alien_0['color'] = 'yellow'
  print("The alien is now " + alien_0['color'] + ".")

  # 删除键-值对 使用del语句
  alien_0 = {'color': 'green', 'points': 5}
  print(alien_0)
  del alien_0['points']
  print(alien_0)

  # 遍历字典  顺序与存储数据未必相同
  user_0 = {
  'username': 'efermi',
  'first': 'enrico',
  'last': 'fermi',
  }
  # Python 字典(Dictionary) items() 函数以列表返回可遍历的(键, 值) 元组数组。
  for key, value in user_0.items():
  	print("\nKey: " + key)
  	print("Value: " + value)

  # 字典的values()方法,返回一个值列表  集合(set)去重  
  favorite_languages = {
  'jen': 'python',
  'sarah': 'c',
  'edward': 'ruby',
  'phil': 'python',
  }
  print("The following languages have been mentioned:")
  for language in set(favorite_languages.values()):
  	print(language.title())    
  ```
- for遍历


## 用户输入 while循环

## 函数

## 类

## 文件和异常





