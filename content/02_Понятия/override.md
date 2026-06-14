---
type: concept
discipline: OOP
language: C#
tags:
  - понятие
---
# override

> [!tip] Простыми словами: `override` — это когда наследник заменяет виртуальный метод родителя своей версией.

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
## Связи
- Связано с: [[4. Полиморфизм]]
- Связано с: [[virtual]]
- Связано с: [[new как скрытие метода]]

## Источник
- файл: `4.tex`
- раздел: Полиморфизм через virtual и override
