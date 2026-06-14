# Program.cs

## Путь

`Interface/Program.cs`

## Назначение

Файл демонстрирует реализацию интерфейсов `ICloneable` и `IComparable` в классе [[Класс — A]].

## Исходный код

```csharp
﻿var a1 = new A(new int[] {3, 5, 7});
var a2 = (A)a1.Clone();
var a3 = a1;
a1[0] = 10;
Console.WriteLine(a1);
Console.WriteLine(a2);
Console.WriteLine(a3);

CompareValues(a1, a2);
CompareValues(33, 161);
CompareValues(a2, 111);

void CompareValues(IComparable a, IComparable b)
{
    if (a.CompareTo(b) < 0)
        Console.WriteLine("a < b");
    else if (a.CompareTo(b) > 0)
        Console.WriteLine("a > b");
    else Console.WriteLine("a == b");
}

class A : ICloneable, IComparable
{
    int[] arr;
    public int this[int i]
    {
        get => arr[i];
        set => arr[i] = value;
    }
    public A(int[] mas)
    {
        arr = (int[])mas.Clone();
    }

    public object Clone()
    {
        return new A(arr);
    }

    public override string ToString()
    {
        return string.Join(", ", arr);
    }

    public int CompareTo(object? obj)
    {
        if (obj is A a)
        {
            return arr.Sum() - a.arr.Sum();
        }
        throw new ArgumentException("Объекты нельзя сравнить");
    }
}
```

## Разбор по блокам

### Блок 1. Клонирование и присваивание ссылки

`a2` получает копию `a1`, а `a3` получает ссылку на тот же объект, что и `a1`.

После `a1[0] = 10` объект `a3` тоже покажет измененное значение, потому что это та же ссылка. `a2` останется отдельной копией.

### Блок 2. `CompareValues`

Метод принимает параметры типа `IComparable`, поэтому может вызвать `CompareTo`.

### Блок 3. Класс `A`

Класс хранит массив, предоставляет индексатор, умеет клонироваться и сравниваться.

## Связи

- Использует: [[Класс — A]], `ICloneable`, `IComparable`.
- Демонстрирует: интерфейсы, индексатор, исключения.

## Что нужно уметь объяснить преподавателю

- Почему `a2` и `a3` ведут себя по-разному.
- Что такое интерфейс.
- Почему `CompareValues` принимает `IComparable`, а не `A`.
- Что делает `Clone`.
- Почему `CompareTo` выбрасывает исключение для неподходящих объектов.

