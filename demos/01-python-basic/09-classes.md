# [Classes](https://docs.python.org/3/tutorial/classes.html#a-first-look-at-classes)


```python
class MyFirstClass:
    def __init__(self, name):
        self.name = name

    def greet(self):
        print('Hello {}!'.format(self.name))
```


```python
my_instance = MyFirstClass('John Doe')
print('my_instance: {}'.format(my_instance))
print('type: {}'.format(type(my_instance)))
print('my_instance.name: {}'.format(my_instance.name))
```

## Métodos
As funções dentro das classes são chamadas de métodos. Eles são usados ​​de forma semelhante como funções.


```python
alice = MyFirstClass(name='Alice')
alice.greet()
```

### `__init__()`
`__init__()` é um método especial que é usado para inicializar instâncias da classe. É chamado quando você cria uma instância da classe.


```python
class Example:
    def __init__(self):
        print('Now we are inside __init__')
        
print('creating instance of Example')
example = Example()
print('instance created')
```

`__init__()` é normalmente usado para inicializar variáveis ​​de instância de sua classe. Estes podem ser listados como argumentos após `self`. Para poder acessar essas variáveis ​​de instância mais tarde durante a vida útil de sua instância, você deve salvá-las em `self`. `self` é o primeiro argumento dos métodos da sua classe e é o seu acesso às variáveis ​​de instância e outros métodos. 


```python
class Example:
    def __init__(self, var1, var2):
        self.first_var = var1
        self.second_var = var2
        
    def print_variables(self):
        print('{} {}'.format(self.first_var, self.second_var))
        
e = Example('abc', 123)
e.print_variables()
    
```

### `__str__()`
`__str__()` é um método especial que é chamado quando uma instância da classe é convertida em string (por exemplo, quando você deseja imprimir a instância). Em outras palavras, definindo o método `__str__` para sua classe, você pode decidir qual é a versão imprimível das instâncias de sua classe. O método deve retornar uma string.


```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def __str__(self):
        return 'Person: {}'.format(self.name)
    
jack = Person('Jack', 82)
print('This is the string presentation of jack: {}'.format(jack))
```

## Variáveis ​​de classe vs variáveis ​​de instância
As variáveis ​​de classe são compartilhadas entre todas as instâncias dessa classe, enquanto as variáveis ​​de instância podem conter valores diferentes entre diferentes instâncias dessa classe.


```python
class Example:
    # Estas são variáveis ​​de classe
    name = 'Example class'
    description = 'Just an example of a simple class'

    def __init__(self, var1):
        # Esta é uma variável de instância
        self.instance_variable = var1

    def show_info(self):
        info = 'instance_variable: {}, name: {}, description: {}'.format(
            self.instance_variable, Example.name, Example.description)
        print(info)


inst1 = Example('foo')
inst2 = Example('bar')

# nome e descrição têm valores idênticos entre instâncias
assert inst1.name == inst2.name == Example.name
assert inst1.description == inst2.description == Example.description

# Se você alterar o valor de uma variável de classe, ele será alterado em todas as instâncias
Example.name = 'Modified name'
inst1.show_info()
inst2.show_info()
```

## Público x privado
Em python, agora há uma separação estrita para métodos privados/públicos ou variáveis ​​de instância. A convenção é iniciar o nome do método ou variável de instância com sublinhado se for tratado como privado. Privado significa que não deve ser acessado de fora da classe.

Por exemplo, vamos considerar que temos uma classe `Person` que tem `age` como variável de instância. Queremos que `age` não seja acessado diretamente (por exemplo, alterado) após a criação da instância. Em Python, isso seria:


```python
class Person:
    def __init__(self, age):
        self._age = age
        
example_person = Person(age=15)
# Você não pode fazer isso:
# print(example_person.age)
# isso também não:
# example_person.age = 16
```

Se você quiser que o `age` seja legível, mas não gravável, você pode usar `property`:


```python
class Person:
    def __init__(self, age):
        self._age = age
        
    @property
    def age(self):
        return self._age
        
example_person = Person(age=15)
# Agora você pode fazer isso:
print(example_person.age)
# Mas não isso:
#example_person.age = 16
```

Dessa forma, você pode ter um acesso controlado às variáveis ​​de instância de sua classe: 


```python
class Person:
    def __init__(self, age):
        self._age = age
        
    @property
    def age(self):
        return self._age
    
    def celebrate_birthday(self):
        self._age += 1
        print('Happy bday for {} years old!'.format(self._age))
        
example_person = Person(age=15)
example_person.celebrate_birthday()
```

## Introdução à herança


```python
class Animal:
    def greet(self):
        print('Hello, I am an animal')

    @property
    def favorite_food(self):
        return 'beef'


class Dog(Animal):
    def greet(self):
        print('wof wof')


class Cat(Animal):
    @property
    def favorite_food(self):
        return 'fish'
```


```python
dog = Dog()
dog.greet()
print("Dog's favorite food is {}".format(dog.favorite_food))

cat = Cat()
cat.greet()
print("Cat's favorite food is {}".format(cat.favorite_food))
```
