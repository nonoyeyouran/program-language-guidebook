# Python 面向对象编程（OOP）

面向对象编程（OOP）是一种编程范式，通过将数据和操作数据的方法封装在对象中，使代码更模块化、可重用和易于维护。Python 是一种支持面向对象编程的语言，以下是 Python 中 OOP 的核心概念和特性。

---

## 1. 类与对象
- **类（Class）**：类是对象的蓝图或模板，定义了对象的属性和方法。
- **对象（Object）**：对象是类的实例，具有类定义的属性和方法。

### 1.1 定义类
使用 `class` 关键字定义类，类名通常采用驼峰命名法（如 `MyClass`）。

### 1.2 创建对象
通过调用类名并传递参数来创建对象。

---

## 2. 类的属性和方法
- **属性**：类的变量，用于存储数据。
- **方法**：类的函数，用于定义对象的行为。

### 2.1 实例属性与方法
- 实例属性：每个对象独有的属性，通过 `self` 关键字定义。
- 实例方法：操作实例属性的方法，第一个参数必须是 `self`。

### 2.2 类属性与方法
- 类属性：类的所有对象共享的属性，直接在类中定义。
- 类方法：操作类属性的方法，使用 `@classmethod` 装饰器定义，第一个参数是 `cls`。

### 2.3 静态方法
- 静态方法：与类和实例无关的方法，使用 `@staticmethod` 装饰器定义，无需 `self` 或 `cls` 参数。

```
class Dog:
    species = "Canis familiaris"  # 类属性

    def __init__(self, name, age):
        self.name = name  # 实例属性
        self.age = age

    def bark(self):  # 实例方法
        print(f"{self.name} is barking!")

    @classmethod
    def get_species(cls):  # 类方法
        return cls.species

    @staticmethod
    def is_dog(animal):  # 静态方法
        return animal.lower() == "dog"

# 使用
my_dog = Dog("Buddy", 3)
print(Dog.get_species())  # 输出: Canis familiaris
print(Dog.is_dog("Dog"))  # 输出: True
```

---

## 3. 构造函数与析构函数
- **构造函数 (`__init__`)**：在创建对象时自动调用，用于初始化对象的属性。
- **析构函数 (`__del__`)**：在对象销毁时自动调用，用于释放资源。
```
class Dog:
    def __init__(self, name):
        self.name = name
        print(f"{self.name} is created!")

    def __del__(self):
        print(f"{self.name} is destroyed!")

# 使用
my_dog = Dog("Buddy")  # 输出: Buddy is created!
del my_dog  # 输出: Buddy is destroyed!
```
---

## 4. 封装
封装是将数据（属性）和操作数据的方法（方法）绑定在一起，并隐藏内部实现细节。

### 4.1 访问控制
- **公有成员**：默认情况下，类的属性和方法是公有的，可以在类外部访问。
- **私有成员**：在属性或方法名前加双下划线 `__`，表示私有成员，只能在类内部访问。
```
class Dog:
    def __init__(self, name, age):
        self.name = name  # 公有属性
        self.__age = age  # 私有属性

    def get_age(self):  # 公有方法
        return self.__age

# 使用
my_dog = Dog("Buddy", 3)
print(my_dog.name)  # 输出: Buddy
print(my_dog.get_age())  # 输出: 3
# print(my_dog.__age)  # 报错: 无法访问私有属性
```
---

## 5. 继承
继承允许一个类（子类）从另一个类（父类）继承属性和方法，从而实现代码重用。

### 5.1 单继承
- 子类继承一个父类的属性和方法。

### 5.2 多继承
- 子类可以继承多个父类的属性和方法。

### 5.3 方法重写
- 子类可以重写父类的方法，以实现不同的行为。

### 5.4 `super()` 函数
- 用于调用父类的方法，通常在子类的构造函数中使用。
```
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} makes a sound.")

class Dog(Animal):  # 单继承
    def speak(self):  # 方法重写
        print(f"{self.name} barks!")

# 使用
my_dog = Dog("Buddy")
my_dog.speak()  # 输出: Buddy barks!
```
---

## 6. 多态
多态是指同一个方法在不同类中具有不同的实现方式。

### 6.1 方法重写实现多态
- 子类重写父类的方法，调用时根据对象的类型执行不同的方法。

### 6.2 鸭子类型
- Python 是一种动态类型语言，不强制要求对象继承自某个类，只要对象具有所需的方法即可。

---

## 7. 特殊方法（魔术方法）
Python 提供了许多特殊方法（以双下划线 `__` 开头和结尾），用于定义类的行为。

### 7.1 常用特殊方法
- `__init__`：构造函数。
- `__del__`：析构函数。
- `__str__`：定义对象的字符串表示形式。
- `__repr__`：定义对象的官方字符串表示形式。
- `__len__`：定义对象的长度。
- `__add__`：定义对象的加法操作。
```
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):
        return f"Point({self.x}, {self.y})"

    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)

# 使用
p1 = Point(1, 2)
p2 = Point(3, 4)
print(p1 + p2)  # 输出: Point(4, 6)
```
---

## 8. 抽象基类
抽象基类（Abstract Base Class, ABC）用于定义接口，要求子类必须实现某些方法。

### 8.1 使用 `abc` 模块
- 通过 `abc.ABC` 和 `@abc.abstractmethod` 定义抽象基类。
```
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        print("Woof!")

# 使用
my_dog = Dog()
my_dog.speak()  # 输出: Woof!
```
---

## 9. 属性装饰器
Python 提供了属性装饰器，用于将方法转换为属性。

### 9.1 `@property`
- 将方法转换为只读属性。

### 9.2 `@属性名.setter`
- 定义属性的设置方法。

### 9.3 `@属性名.deleter`
- 定义属性的删除方法。

```
class Dog:
    def __init__(self, name):
        self._name = name

    @property
    def name(self):
        return self._name

    @name.setter
    def name(self, value):
        self._name = value

    @name.deleter
    def name(self):
        del self._name

# 使用
my_dog = Dog("Buddy")
print(my_dog.name)  # 输出: Buddy
my_dog.name = "Max"
print(my_dog.name)  # 输出: Max
del my_dog.name
```
---

## 10. 类的组合与聚合
- **组合**：一个类的对象是另一个类的组成部分，生命周期一致。
- **聚合**：一个类的对象包含另一个类的对象，生命周期不一致。
```
class Engine:
    def start(self):
        print("Engine started.")

class Car:
    def __init__(self):
        self.engine = Engine()  # 组合

    def start(self):
        self.engine.start()
        print("Car started.")

# 使用
my_car = Car()
my_car.start()  # 输出: Engine started. Car started.
```
---

## 总结
Python 的面向对象编程提供了强大的工具来组织代码，包括类与对象、封装、继承、多态、特殊方法等。掌握这些概念和特性可以帮助你编写更模块化、可重用和易于维护的代码。
