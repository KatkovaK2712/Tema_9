# Тема 9. Концепции и принципы ООП
Отчет по Теме #9 выполнил(а):
- Каткова Ксения Александровна
- ПИЭ-22-1

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |

знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1
Допустим, что вы решили оригинально и немного странно познакомится с человеком. Для этого у вас должен быть написан свой класс на Python, который будет проверять угадал ваше имя человек или нет. Для этого создайте класс, указав в свойствах только имя. Дальше создайте функцию init (), а в ней сделайте проверку на то угадал человек ваше имя или нет. Также можете проверить что будет, если в этой функции указав атрибут, который не указан в вашем классе, например, попробуйте вызвать фамилию.

```python
class Person:
    def __init__(self, name):
        self.name = name
    def guess_name(self, guessed_name):
        if guessed_name == self.name:
            return "Вы угадали мое имя!"
        else:
            return "Вы не угадали мое имя."

person = Person("Алексей")
a = input("Введите имя: ")
print(person.guess_name(a))
```
### Результат.
![image](https://github.com/user-attachments/assets/470f70eb-aa4b-4925-bc98-a58178cef2a4)

## Выводы
- __init__(self, name): конструктор, который принимает имя и сохраняет его в атрибуте name.
- guess_name(self, guessed_name): метод, который проверяет, совпадает ли введённое имя с сохранённым именем, и возвращает соответствующее сообщение.
С помощью этих методов осуществляется проверка, угадал ли пользователь имя человека, заданное при создании объекта Person.

## Лабораторная работа №2
Вам дали важное задание, написать продавцу мороженого программу, которая будет писать добавили ли топпинг в мороженое и цену после возможного изменения. Для этого вам нужно написать класс, в котором будет определяться изменили ли состав мороженого или нет. В этом классе реализуйте метод, выводящий на печать «Мороженое с {ТОППИНГ}» в случае наличия добавки, а иначе отобразится следующая фраза: «Обычное мороженое». При этом программа должна воспринимать как топпинг только атрибуты типа string.

```python
class IceCream:
    def __init__(self, topping=None):
        self.topping = topping
    def display(self):
        if isinstance(self.topping, str):
            print(f"Мороженое с {self.topping}")
        else:
            print("Обычное мороженое")
ice_cream1 = IceCream("шоколадом")
ice_cream1.display()
```
### Результат.
![image](https://github.com/user-attachments/assets/034ca6f8-318f-42f5-9cca-d8a1b09afc63)

## Выводы
Код демонстрирует простую реализацию класса IceCream, который может иметь дополнительные ингредиенты (топпинги), и предоставляет способ отображать информацию о мороженом.

## Лабораторная работа №3
Петя – начинающий программист и на занятиях ему сказали реализовать икапсу…что-то. А вы хороший друг Пети и ко всему прочему прекрасно знаете, что икапсу…что-то – это инкапсуляция, поэтому решаете помочь вашему другу с написанием класса с инкапсуляцией. Ваш класс будет не просто инкапсуляцией, а классом с сеттером, геттером и деструктором. После написания класса вам необходимо продемонстрировать что все написанные вами функции работают.

```python
class Encapsulation:
    def __init__(self, value):
        self.__value = value
    def set_value(self, value):
        self.__value = value
    def get_value(self):
        return self.__value
    def __del__(self):
        print(f"Объект с значением {self.__value} был уничтожен.")
encapsulation = Encapsulation(10)
print(encapsulation.get_value())
encapsulation.set_value(20)
print(encapsulation.get_value())
del encapsulation
```
### Результат.
![image](https://github.com/user-attachments/assets/c17ca1a9-6183-4a29-a48c-34a603005a62)

## Выводы
Код демонстрирует принцип инкапсуляции в Python, где доступ к приватному полю осуществляется только через специальные методы set_value() и get_value().

## Лабораторная работа №4
Вам прекрасно известно, что кошки и собаки являются млекопитающими, но компьютер этого не понимает, поэтому вам нужно написать три класса: Кошки, Собаки, Млекопитающие. И при помощи “наследования” объяснить компьютеру что кошки и собаки – это млекопитающие. Также добавьте какой-нибудь свой атрибут для кошек и собак, чтобы показать, что они чем-то отличаются друг от друга.

```python
class Mammal:
    def __init__(self, species):
        self.species = species
class Cat(Mammal):
    def __init__(self, name):
        super().__init__("Кошка")
        self.name = name
class Dog(Mammal):
    def __init__(self, name):
        super().__init__("Собака")
        self.name = name
cat = Cat("Мурка")
dog = Dog("Шарик")
print(f"{cat.name} - {cat.species}")
print(f"{dog.name} - {dog.species}")
```
### Результат.
![image](https://github.com/user-attachments/assets/23503d07-0bac-4315-b88a-0315494faccd)

## Выводы
- Создан базовый класс Mammal, который имеет атрибут species.
- Созданы два дочерних класса Cat и Dog, которые наследуются от Mammal. В конструкторах этих классов вызывается конструктор базового класса с передачей соответствующих видов животных.
- Создаются объекты cat и dog классов Cat и Dog соответственно, с указанием имен.

## Лабораторная работа №5
На разных языках здороваются по-разному, но суть остается одинаковой, люди друг с другом здороваются. Давайте вместе с вами реализуем программу с полиморфизмом, которая будет описывать всю суть первого предложения задачи. Для этого мы можем выбрать два языка, например, русский и английский и написать для них отдельные классы, в которых будет в виде атрибута слово, которым здороваются на этих языках. А также напишем функцию, которая будет выводить информацию о том, как на этих языках здороваются.
Заметьте, что для решения поставленной задачи мы использовали декоратор @staticmethod, поскольку нам не нужны обязательные параметры-ссылки вроде self.

```python
class RussianGreeting:
    greeting = "Привет"
    @staticmethod
    def greet():
        return RussianGreeting.greeting
class EnglishGreeting:
    greeting = "Hello"
    @staticmethod
    def greet():
        return EnglishGreeting.greeting
def greet_in_languages():
    print(RussianGreeting.greet())
    print(EnglishGreeting.greet())
greet_in_languages()
```
### Результат.

## Выводы
Код демонстрирует пример использования статических методов и переменных в Python для реализации приветствий на разных языках.


## Самостоятельная работа №1


```python

```
### Результат.

## Выводы


## Самостоятельная работа №2


```python

```
### Результат.

## Выводы


## Самостоятельная работа №3


```python

```
### Результат.

## Выводы


## Самостоятельная работа №4


```python

```
### Результат.

## Выводы


## Самостоятельная работа №5


```python

```
### Результат.

## Выводы


## Самостоятельная работа №6


```python

```
### Результат.

## Выводы


## Самостоятельная работа №7


```python

```
### Результат.

## Выводы


## Самостоятельная работа №8


```python

```
### Результат.

## Выводы


## Самостоятельная работа №9


```python

```
### Результат.

## Выводы


## Самостоятельная работа №10


```python

```
### Результат.

## Выводы


## Общие выводы по теме