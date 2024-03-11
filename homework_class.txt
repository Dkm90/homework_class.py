# 1.	Создать класс с двумя переменными. Добавить функцию вывода на экран и функцию изменения этих переменных.
# Добавить функцию, которая находит сумму значений этих переменных, и функцию которая находит наибольшее значение из
# этих двух переменных.

class SomeClass:
    var_1 = 7
    var_2 = 14

    def __init__(self, var_1, var_2):
        self.var_1 = var_1
        self.var_2 = var_2

    def print(self):
        print(self.var_1)
        print(self.var_2)


    def summ(self):
        print(self.var_1 + self.var_2)


    def max_number(self, var_1, var_2):
        if self.var_1 > self.var_2:
            print(self.var_1)
        else:
            print(self.var_2)


# 2.	Описать класс, реализующий десятичный счетчик, который может увеличивать или уменьшать свое значение на единицу
# в заданном диапазоне. Предусмотреть инициализацию счетчика значениями по умолчанию и произвольными значениями.
# Счетчик имеет два метода: увеличения и уменьшения, — и свойство, позволяющее получить его текущее состояние.
# Написать программу, демонстрирующую все возможности класса.

class Counter:
    current = 0
    def __init__(self, start=None, end=None):
        self.start = start
        self.end = end

    def increase(self):
        if self.current < self.end:
            self.current += 1
            return self.current
        else:
            return 'Out of range'


    def decrease(self):
        if self.start > self.end:
            self.start -= 1
            return self.start
        else:
            return 'Out of range'

my_count=Counter(start=0, end=3)
print(my_count.increase())
print(my_count.increase())
print(my_count.increase())
print(my_count.increase())

my_count = Counter(start=3, end=0)
print(my_count.decrease())
print(my_count.decrease())
print(my_count.decrease())
print(my_count.decrease())

# 3.	Реализуйте класс Shop. Предусмотреть возможность работы с произвольным числом продуктов,
# поиска продуктов по названию, добавления их в магазин и удаления продуктов из него.

class Shop:
    def __init__(self):
        self.products = []

    def add_product(self, product):
        self.products.append(product)

    def remove_product(self, product):
        if product in self.products:
            self.products.remove(product)

    def find_product_by_name(self, name):
        found_products = []
        for product in self.products:
            if product['name'] == name:
                found_products.append(product)
        return found_products

my_shop = Shop()

my_shop.add_product({'name': 'apple', 'price': 1.5})
my_shop.add_product({'name': 'banana', 'price': 2.0})
my_shop.add_product({'name': 'orange', 'price': 1.0})


apples = my_shop.find_product_by_name('apple')
print(apples)

my_shop.remove_product({'name': 'banana', 'price': 2.0})

bananas = my_shop.find_product_by_name('banana')
print(bananas)

# 4.	Реализуйте класс MoneyBox, для работы с виртуальной копилкой. Каждая копилка имеет ограниченную вместимость,
# которая выражается целым числом – количеством монет(capacity -вместимость), которые можно положить в копилку.
# Класс должен поддерживать информацию о количестве монет в копилке, предоставлять возможность добавлять монеты в
# копилку и узнавать, можно ли добавить в копилку ещё какое-то количество монет, не превышая ее вместимость.

class MoneyBox:
    def __init__(self, capacity):
        self.capacity = capacity
        self.coins = 0

    def can_add(self, count):
        return self.coins + count <= self.capacity

    def add(self, count):
        if self.can_add(count):
            self.coins += count
            print("Монеты  добавлены")
        else:
            print("Копилка заполнена!")


box = MoneyBox(10)
box.add(5)
box.add(8)
box.add(2)
