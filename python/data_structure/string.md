# Python 字符串常用操作详解

## 目录
1. [字符串的创建](#字符串的创建)
2. [字符串的访问](#字符串的访问)
3. [字符串的修改](#字符串的修改)
4. [字符串的查找与替换](#字符串的查找与替换)
5. [字符串的分割与连接](#字符串的分割与连接)
6. [字符串的格式化](#字符串的格式化)
7. [字符串的常用方法](#字符串的常用方法)
8. [总结](#总结)

---

## 字符串的创建
Python 中的字符串可以通过单引号、双引号或三引号创建：
- 单引号：`'Hello, World!'`
- 双引号：`"Hello, World!"`
- 三引号（多行字符串）：  
`'''Hello,`  
`World!'''`
---

## 字符串的访问
- 通过索引访问单个字符：
`s = "Python"`
`print(s[0])`  # 输出: P
- 通过切片访问子字符串：
`print(s[1:4])`  # 输出: yth
- 负数索引表示从末尾开始：
`print(s[-1])`  # 输出: n

---

## 字符串的修改
- 字符串是不可变的，不能直接修改某个字符。可以通过拼接或替换生成新字符串。
- 示例：
`s = "Python"`
`s = s[:1] + 'i' + s[2:]`  # 修改为: Pithon

---

## 字符串的查找与替换

### 查找
- `find()`：查找子字符串，返回第一次出现的索引，未找到返回 `-1`。
`s = "Hello, World!"`
`print(s.find("World"))`  # 输出: 7
- `index()`：与 `find()` 类似，但未找到时抛出异常。
`print(s.index("World"))`  # 输出: 7

### 替换
- `replace()`：替换字符串中的子字符串。
`s = "Hello, World!"`
`s = s.replace("World", "Python")`  # 输出: Hello, Python!

---

## 字符串的分割与连接

### 分割
- `split()`：根据分隔符分割字符串，返回列表。
`s = "apple,banana,orange"`
`print(s.split(","))`  # 输出: ['apple', 'banana', 'orange']

### 连接
- `join()`：将列表中的字符串连接成一个字符串。
`lst = ['apple', 'banana', 'orange']`
`print(",".join(lst))`  # 输出: apple,banana,orange

---

## 字符串的格式化

### 1. 使用 `%` 格式化
- 示例：
`name = "Alice"`
`age = 25`
`print("Name: %s, Age: %d" % (name, age))`  # 输出: Name: Alice, Age: 25

### 2. 使用 `str.format()` 格式化
- 示例：
`print("Name: {}, Age: {}".format(name, age))`  # 输出: Name: Alice, Age: 25

### 3. 使用 f-string 格式化（Python 3.6+）
- 示例：
`print(f"Name: {name}, Age: {age}")`  # 输出: Name: Alice, Age: 25

---

## 字符串的常用方法

### 1. 大小写转换
- `upper()`：转换为大写。
`s = "Python"`
`print(s.upper())`  # 输出: PYTHON
- `lower()`：转换为小写。
`print(s.lower())`  # 输出: python
- `title()`：每个单词首字母大写。
`s = "hello world"`
`print(s.title())`  # 输出: Hello World

### 2. 去除空白字符
- `strip()`：去除两端空白字符。
`s = "  Python  "`
`print(s.strip())`  # 输出: Python
- `lstrip()`：去除左侧空白字符。
- `rstrip()`：去除右侧空白字符。

### 3. 判断字符串内容
- `isalpha()`：判断是否全为字母。
`s = "Python"`
`print(s.isalpha())`  # 输出: True
- `isdigit()`：判断是否全为数字。
`s = "123"`
`print(s.isdigit())`  # 输出: True
- `isalnum()`：判断是否全为字母或数字。
`s = "Python123"`
`print(s.isalnum())`  # 输出: True

### 4. 统计子字符串出现次数
- `count()`：统计子字符串出现的次数。
`s = "Hello, World!"`
`print(s.count("l"))`  # 输出: 3

---

## 总结
- Python 字符串是不可变的，但提供了丰富的操作方法。
- 常用操作包括创建、访问、修改、查找、替换、分割、连接和格式化。
- 掌握这些操作可以高效地处理字符串数据。

---

通过以上内容，您可以快速掌握 Python 中字符串的基本用法，并应用于实际开发中。
