# Python 文件操作

文件操作是编程中常见的任务之一，Python 提供了丰富的内置函数和模块来处理文件的读写、管理和操作。以下是 Python 文件操作的核心内容。

---

## 1. 文件的打开与关闭

### 1.1 打开文件
- 使用 `open()` 函数打开文件，返回一个文件对象。
- `open()` 函数的参数：
  - `file`：文件路径（字符串）。
  - `mode`：文件打开模式（如 `'r'` 表示只读，`'w'` 表示写入）。
  - `encoding`：文件编码（如 `'utf-8'`）。

### 1.2 文件打开模式
- `'r'`：只读模式（默认）。
- `'w'`：写入模式，覆盖文件内容。
- `'a'`：追加模式，在文件末尾添加内容。
- `'x'`：独占创建模式，文件已存在时抛出错误。
- `'b'`：二进制模式（如 `'rb'` 或 `'wb'`）。
- `'t'`：文本模式（默认）。
- `'+'`：读写模式（如 `'r+'` 或 `'w+'`）。

### 1.3 关闭文件
- 使用文件对象的 `close()` 方法关闭文件。
- 推荐使用 `with` 语句自动管理文件的打开和关闭。
```
file = open("example.txt", "r", encoding="utf-8")
file.close()

with open("example.txt", "r", encoding="utf-8") as file:
    content = file.read()
```
---

## 2. 文件的读写操作

### 2.1 读取文件
- `read()`：读取文件的全部内容。
- `readline()`：读取文件的一行内容。
- `readlines()`：读取文件的所有行，返回列表。
```
with open("example.txt", "r", encoding="utf-8") as file:
    content = file.read()  # 读取全部内容
    line = file.readline()  # 读取一行内容
    lines = file.readlines()  # 读取所有行
```
### 2.2 写入文件
- `write()`：将字符串写入文件。
- `writelines()`：将字符串列表写入文件。
```
with open("example.txt", "w", encoding="utf-8") as file:
    file.write("Hello, World!")  # 写入字符串
    file.writelines(["Line 1\n", "Line 2\n"])  # 写入字符串列表
```
### 2.3 文件指针操作
- `seek(offset, whence)`：移动文件指针到指定位置。
  - `offset`：偏移量。
  - `whence`：参考位置（`0` 表示文件开头，`1` 表示当前位置，`2` 表示文件末尾）。
- `tell()`：返回文件指针的当前位置。
```
with open("example.txt", "r", encoding="utf-8") as file:
    file.seek(10)  # 移动文件指针到第 10 个字节
    position = file.tell()  # 获取当前文件指针位置
```
---

## 3. 文件与目录管理

### 3.1 `os` 模块
- 提供与操作系统交互的功能。
- 常用函数：
  - `os.rename()`：重命名文件或目录。
  - `os.remove()`：删除文件。
  - `os.mkdir()`：创建目录。
  - `os.rmdir()`：删除空目录。
  - `os.listdir()`：列出目录内容。
  - `os.path.exists()`：检查文件或目录是否存在。
  - `os.path.isfile()`：检查是否为文件。
  - `os.path.isdir()`：检查是否为目录。
```
import os

os.rename("old.txt", "new.txt")  # 重命名文件
os.remove("file.txt")  # 删除文件
os.mkdir("new_dir")  # 创建目录
os.rmdir("empty_dir")  # 删除空目录
files = os.listdir(".")  # 列出目录内容
exists = os.path.exists("file.txt")  # 检查文件或目录是否存在
```
### 3.2 `shutil` 模块
- 提供高级文件操作功能。
- 常用函数：
  - `shutil.copy()`：复制文件。
  - `shutil.move()`：移动文件或目录。
  - `shutil.rmtree()`：递归删除目录及其内容。
```
import shutil

shutil.copy("source.txt", "destination.txt")  # 复制文件
shutil.move("source.txt", "destination.txt")  # 移动文件或目录
shutil.rmtree("dir")  # 递归删除目录及其内容
```
---

## 4. 文件路径操作

### 4.1 `os.path` 模块
- 提供路径操作的功能。
- 常用函数：
  - `os.path.join()`：拼接路径。
  - `os.path.abspath()`：获取绝对路径。
  - `os.path.dirname()`：获取目录名。
  - `os.path.basename()`：获取文件名。
  - `os.path.split()`：分割路径为目录和文件名。
  - `os.path.splitext()`：分割文件名和扩展名。
```
import os

path = os.path.join("dir", "file.txt")  # 拼接路径
abs_path = os.path.abspath("file.txt")  # 获取绝对路径
dirname = os.path.dirname("dir/file.txt")  # 获取目录名
basename = os.path.basename("dir/file.txt")  # 获取文件名
dir, file = os.path.split("dir/file.txt")  # 分割路径为目录和文件名
name, ext = os.path.splitext("file.txt")  # 分割文件名和扩展名
```

### 4.2 `pathlib` 模块
- 提供面向对象的路径操作方式。
- 常用类：
  - `Path`：表示文件系统路径。
  - 支持路径拼接、文件检查、路径解析等操作。
```
from pathlib import Path

path = Path("dir/file.txt")
path.exists()  # 检查路径是否存在
path.is_file()  # 检查是否为文件
path.is_dir()  # 检查是否为目录
new_path = path.with_name("new_file.txt")  # 修改文件名
```
---

## 5. 文件编码与解码

### 5.1 文本文件编码
- 文本文件通常使用某种字符编码（如 `utf-8`）。
- 在打开文件时指定 `encoding` 参数。
```
with open("example.txt", "r", encoding="utf-8") as file:
    content = file.read()
```
### 5.2 二进制文件
- 二进制文件以字节形式存储数据。
- 使用 `'b'` 模式打开文件。
```
with open("example.bin", "rb") as file:
    data = file.read()
```
---

## 6. 文件操作的异常处理

### 6.1 常见异常
- `FileNotFoundError`：文件不存在。
- `PermissionError`：没有文件操作权限。
- `IsADirectoryError`：尝试对目录执行文件操作。

### 6.2 使用 `try-except` 处理异常
- 捕获并处理文件操作中的异常，确保程序健壮性。
```
try:
    with open("example.txt", "r", encoding="utf-8") as file:
        content = file.read()
except FileNotFoundError:
    print("文件不存在")
except PermissionError:
    print("没有文件操作权限")
```
---

## 7. 临时文件与目录

### 7.1 `tempfile` 模块
- 提供创建临时文件和目录的功能。
- 常用函数：
  - `tempfile.mkstemp()`：创建临时文件。
  - `tempfile.mkdtemp()`：创建临时目录。
  - `tempfile.TemporaryFile()`：创建临时文件对象，自动删除。
```
import tempfile

with tempfile.TemporaryFile() as temp_file:
    temp_file.write(b"Hello, World!")
    temp_file.seek(0)
    print(temp_file.read())
```
---

## 8. 文件压缩与解压

### 8.1 `zipfile` 模块
- 提供 ZIP 文件的读写功能。
- 常用类：
  - `ZipFile`：表示 ZIP 文件对象。
  - 支持文件的压缩、解压和查看。
```
import zipfile

# 压缩文件
with zipfile.ZipFile("archive.zip", "w") as zipf:
    zipf.write("file.txt")

# 解压文件
with zipfile.ZipFile("archive.zip", "r") as zipf:
    zipf.extractall("extracted")
```
### 8.2 `tarfile` 模块
- 提供 TAR 文件的读写功能。
- 常用类：
  - `TarFile`：表示 TAR 文件对象。
  - 支持文件的压缩、解压和查看。
```
import tarfile

# 压缩文件
with tarfile.open("archive.tar.gz", "w:gz") as tarf:
    tarf.add("file.txt")

# 解压文件
with tarfile.open("archive.tar.gz", "r:gz") as tarf:
    tarf.extractall("extracted")
```
---

## 总结
Python 提供了丰富的文件操作功能，包括文件的读写、路径管理、目录操作、异常处理等。通过合理使用这些工具，可以高效地处理文件相关的任务。理解文件操作的核心概念和方法，是编写健壮和高效程序的关键。
