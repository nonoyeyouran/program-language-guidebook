# Python 正则表达式用法详解

## 目录
1. [正则表达式简介](#正则表达式简介)
2. [常用正则语法](#常用正则语法)
3. [Python 正则模块](#python-正则模块)
4. [常用函数](#常用函数)
   - [re.match](#re-match)
   - [re.search](#re-search)
   - [re.findall](#re-findall)
   - [re.sub](#re-sub)
   - [re.split](#re-split)
5. [正则表达式示例](#正则表达式示例)
6. [总结](#总结)

---

## 正则表达式简介
正则表达式（Regular Expression，简称 regex）是一种用于匹配字符串的模式。通过特定的语法规则，可以快速查找、替换或提取字符串中的内容。

---

## 常用正则语法

| 语法          | 说明                                                                 |
|---------------|----------------------------------------------------------------------|
| `.`           | 匹配任意字符（除换行符 `\n` 外）。                                   |
| `\d`          | 匹配数字（等价于 `[0-9]`）。                                         |
| `\D`          | 匹配非数字字符。                                                     |
| `\w`          | 匹配字母、数字或下划线（等价于 `[a-zA-Z0-9_]`）。                    |
| `\W`          | 匹配非字母、数字或下划线的字符。                                     |
| `\s`          | 匹配空白字符（包括空格、制表符、换行符等）。                         |
| `\S`          | 匹配非空白字符。                                                     |
| `[]`          | 匹配括号内的任意一个字符。例如 `[abc]` 匹配 `a`、`b` 或 `c`。        |
| `[^]`         | 匹配不在括号内的任意一个字符。例如 `[^abc]` 匹配非 `a`、`b`、`c` 的字符。 |
| `*`           | 匹配前面的字符 0 次或多次。                                          |
| `+`           | 匹配前面的字符 1 次或多次。                                          |
| `?`           | 匹配前面的字符 0 次或 1 次。                                         |
| `{n}`         | 匹配前面的字符恰好 n 次。                                            |
| `{n,}`        | 匹配前面的字符至少 n 次。                                            |
| `{n,m}`       | 匹配前面的字符至少 n 次，至多 m 次。                                 |
| `^`           | 匹配字符串的开头。                                                   |
| `$`           | 匹配字符串的结尾。                                                   |
| `|`           | 匹配左边或右边的表达式。例如 `a|b` 匹配 `a` 或 `b`。                 |
| `()`          | 分组，捕获匹配的内容。                                               |
| `\`           | 转义字符，用于匹配特殊字符。例如 `\.` 匹配句点 `.`。                 |

---

## Python 正则模块
Python 通过 `re` 模块支持正则表达式。使用前需要导入：
`import re`

---

## 常用函数

### re.match
- **功能**：从字符串的开头匹配正则表达式。
- **返回值**：匹配成功返回 `re.Match` 对象，否则返回 `None`。
- **示例**：
  `result = re.match(r'\d+', '123abc')`
  `if result:`
      `print("匹配成功:", result.group())`  # 输出: 匹配成功: 123

### re.search
- **功能**：在字符串中搜索匹配正则表达式的第一个位置。
- **返回值**：匹配成功返回 `re.Match` 对象，否则返回 `None`。
- **示例**：
  `result = re.search(r'\d+', 'abc123def')`
  `if result:`
      `print("匹配成功:", result.group())`  # 输出: 匹配成功: 123

### re.findall
- **功能**：查找字符串中所有匹配正则表达式的内容。
- **返回值**：返回匹配结果的列表。
- **示例**：
  `result = re.findall(r'\d+', 'abc123def456')`
  `print(result)`  # 输出: ['123', '456']

### re.sub
- **功能**：替换字符串中匹配正则表达式的内容。
- **返回值**：返回替换后的字符串。
- **示例**：
  `result = re.sub(r'\d+', 'NUM', 'abc123def456')`
  `print(result)`  # 输出: abcNUMdefNUM

### re.split
- **功能**：根据正则表达式分割字符串。
- **返回值**：返回分割后的列表。
- **示例**：
  `result = re.split(r'\d+', 'abc123def456ghi')`
  `print(result)`  # 输出: ['abc', 'def', 'ghi']

---

## 正则表达式示例

### 1. 匹配邮箱地址
`email = "user@example.com"`
`pattern = r'[\w\.-]+@[\w\.-]+'`
`result = re.match(pattern, email)`
`if result:`
    `print("匹配成功:", result.group())`

### 2. 提取日期
`text = "Today is 2023-10-10."`
`pattern = r'\d{4}-\d{2}-\d{2}'`
`result = re.search(pattern, text)`
`if result:`
    `print("提取的日期:", result.group())`

### 3. 替换敏感词
`text = "This is a bad word."`
`pattern = r'bad'`
`result = re.sub(pattern, '***', text)`
`print(result)`  # 输出: This is a *** word.

### 4. 分割字符串
`text = "apple,banana,orange"`
`pattern = r','`
`result = re.split(pattern, text)`
`print(result)`  # 输出: ['apple', 'banana', 'orange']

---

## 总结
- 正则表达式是处理字符串的强大工具，Python 的 `re` 模块提供了丰富的函数支持。
- 常用函数包括 `re.match`、`re.search`、`re.findall`、`re.sub` 和 `re.split`。
- 掌握正则语法和函数用法，可以高效地完成字符串匹配、提取和替换等操作。

---

通过以上内容，您可以快速掌握 Python 中正则表达式的基本用法，并应用于实际开发中。
