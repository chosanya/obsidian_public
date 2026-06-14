---
type: code-example
discipline: OOP
language: C#
tags:
  - пример-кода
---
# Animal Dog Cat - полиморфизм

> [!tip] Простыми словами: Пример показывает, как разные животные вызываются через общий тип, но звучат по-разному.

## Полиморфизм

> [!definition]
> Полиморфизм — это принцип ООП, позволяющий работать с объектами разных производных классов через общий базовый тип, при этом каждый объект может выполнять действие по-своему.

Проще:

Мы вызываем один и тот же метод одинаковым образом, но результат зависит от реального типа объекта.

**Пример без полиморфизма**

```csharp
public class Dog
{
    public void MakeSound()
    {
        Console.WriteLine("Гав");
    }
}
public class Cat
{
    public void MakeSound()
    {
        Console.WriteLine("Мяу");
    }
}
```

Методы называются одинаково, но классы никак не связаны.
Для каждого типа пришлось бы писать отдельный код:

Dog dog = new Dog();
Cat cat = new Cat();
dog.MakeSound();
cat.MakeSound();

Это ещё не полноценный полиморфизм через наследование.

### Полиморфизм через virtual и override

**Базовый класс:**

```csharp
public class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Животное издаёт звук");
    }
}
```

virtual означает: Этот метод разрешено переопределить в производном классе.

**Производный класс:**

```csharp
public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Гав");
    }
}
```

override означает: Производный класс предоставляет собственную реализацию унаследованного виртуального метода.

**Другой производный класс:**

```csharp
public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Мяу");
    }
}
```

Использование:

- Animal firstAnimal = new Dog();
- Animal secondAnimal = new Cat();
- firstAnimal.MakeSound();
- secondAnimal.MakeSound();

Результат: Гав Мяу

Хотя обе переменные имеют тип Animal, вызывается реализация реального объекта.
-- внутри firstAnimal находится объект Dog; 
-- внутри secondAnimal находится объект Cat. 
Это и есть полиморфизм.

Очень важная строка
Animal animal = new Dog();

Слева: Animal — тип переменной.

Справа: new Dog() — реальный созданный объект.

Переменная базового типа может хранить ссылку на объект производного класса.

Через такую переменную доступны только элементы, объявленные в базовом типе: 
 animal.MakeSound();

Но если метод виртуальный, выбирается реализация по реальному типу объекта.

### Что произойдёт без virtual и override

```csharp
public class Animal
{
    public void MakeSound()
    {
        Console.WriteLine("Животное");
    }
}
public class Dog : Animal
{
    public void MakeSound()
    {
        Console.WriteLine("Гав");
    }
}
```

Теперь:
Animal animal = new Dog();
animal.MakeSound();
будет вызван метод Animal: Животное. Потому что метод базового класса не является виртуальным.

Компилятор также предупредит, что метод Dog.MakeSound() скрывает унаследованный метод.

**Для явного скрытия используют new:**

```csharp
public class Dog : Animal
{
    public new void MakeSound()
    {
        Console.WriteLine("Гав");
    }
}
```

Но это не переопределение.

### Переопределение и скрытие

> [!definition]
> Переопределение: 
> public virtual void MakeSound() 
> public override void MakeSound() 
> Выбор метода зависит от реального типа объекта.

> [!definition]
> Скрытие: 
> public void MakeSound() 
> public new void MakeSound() 
> Выбор зависит от типа переменной.

Пример:

```csharp
Dog dog = new Dog();
Animal animal = new Dog();
dog.MakeSound();
animal.MakeSound();
```

При скрытии методы могут сработать по-разному: Гав, Животное

*Это очень вероятный дополнительный вопрос преподавателя, судя по отзывам.*

### Виртуальный и переопределённый метод

Виртуальный метод объявляется в базовом классе: public virtual void MakeSound()

Переопределённый метод объявляется в производном классе: public override void MakeSound()

Точная формулировка:

> [!definition]
> Виртуальный метод — это метод базового класса, который допускает изменение реализации в производных классах. Переопределённый метод — это новая реализация виртуального метода в производном классе.

**Можно ли вызвать базовую реализацию?**

```csharp
Да, через base:

public class Dog : Animal
{
    public override void MakeSound()
    {
        base.MakeSound();
        Console.WriteLine("Гав");
    }
}
```

Теперь сначала выполнится метод Animal, затем код Dog.

### Полиморфная коллекция

```csharp
List<Animal> animals = new List<Animal>
{
    new Dog(),
    new Cat()
};
foreach (Animal animal in animals)
{
    animal.MakeSound();
}
```

В одной коллекции хранятся объекты разных производных классов, но обращение к ним выполняется через общий тип Animal.

Результат: Гав Мяу -- Это типичный пример полиморфизма.

**Итог** 
Полиморфизм — это принцип ООП, позволяющий использовать объекты разных производных классов через общий базовый тип. При вызове виртуального метода выполняется переопределённая реализация, соответствующая реальному типу объекта. Для этого в базовом классе используется virtual, а в производном — override.

**Короткий ответ** 
Полиморфизм означает «один интерфейс — разные реализации». Например, переменная типа Animal может хранить объект Dog или Cat. При вызове виртуального метода MakeSound собака выведет «Гав», а кошка — «Мяу».

### Почему Animal может хранить Dog?

Потому что Dog наследуется от Animal: public class Dog : Animal

Это означает, что любой объект Dog одновременно является объектом типа Animal.

Логика такая: Каждая собака является животным, но не каждое животное является собакой.

Поэтому допустимо: Animal animal = new Dog();

Но обратное без явного преобразования недопустимо: Dog dog = new Animal(); // ошибка

Обычная переменная Animal знает только о членах, объявленных в Animal.

Например:

```csharp
% public class Animal
% {
%     public void Eat()
%     {
%     }
% }
% public class Dog : Animal
% {
%     public void Bark()
%     {
%     }
% }
% Animal animal = new Dog();
% animal.Eat();  // можно
% animal.Bark(); // ошибка
```

Объект внутри — Dog, но переменная имеет тип Animal, поэтому через неё видны только возможности базового типа.

При этом для виртуальных методов реальный тип объекта всё равно учитывается.

**Итог**

Переменная базового типа может хранить ссылку на объект производного класса, потому что объект производного класса является частным случаем базового типа.

###  override и new

Переопределение через override

```csharp
% public class Animal
% {
%     public virtual void MakeSound()
%     {
%         Console.WriteLine("Животное");
%     }
% }
% public class Dog : Animal
% {
%     public override void MakeSound()
%     {
%         Console.WriteLine("Гав");
%     }
% }

Dog dog = new Dog();
Animal animal = new Dog();
dog.MakeSound();
animal.MakeSound();

Результат:

Гав

Гав
```

Почему: метод переопределён, поэтому реализация выбирается по реальному типу объекта. Реальный объект в обоих случаях — Dog.

### Скрытие через new

```csharp
public class Animal
{
    public void MakeSound()
    {
        Console.WriteLine("Животное");
    }
}
public class Dog : Animal
{
    public new void MakeSound()
    {
        Console.WriteLine("Гав");
    }
}
Dog dog = new Dog();
Animal animal = new Dog();
dog.MakeSound();
animal.MakeSound();

Результат:

Гав

Животное
```

Почему:
-- переменная dog имеет тип Dog, поэтому вызывается метод Dog;
-- переменная animal имеет тип Animal, поэтому вызывается метод Animal.

При new метод потомка не заменяет виртуальное поведение базового метода. Он только скрывает метод с таким же именем.

Главное различие:
При override выбор метода зависит от реального типа объекта. При new выбор зависит от типа переменной.

**Короткая шпаргалка:**
virtual + override → настоящий полиморфизм 
new → скрытие метода 
**итог**

override переопределяет виртуальный метод базового класса. При вызове выбирается реализация по реальному типу объекта. new только скрывает унаследованный метод, поэтому вызываемый вариант зависит от типа переменной.
## Связи
- Связано с: [[4. Полиморфизм]]
- Связано с: [[virtual]]
- Связано с: [[override]]

## Источник
- файл: `4.tex`
- раздел: Полиморфизм
