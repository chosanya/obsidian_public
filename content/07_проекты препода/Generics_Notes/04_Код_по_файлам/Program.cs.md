# Program.cs

## Путь

`Generics/Program.cs`

## Назначение

Файл демонстрирует обобщенный класс `A<T>` и плохую альтернативу `ABad` на `object[]`.

## Исходный код

```csharp
﻿var a1 = new A<int>([2, 5, 7]);
var a2 = new A<double>([2.5, 4.11, 3.55]);
var a3 = new A<int>([8, 7, 12]);
var a4 = new A<A<int>>([a1, a3]);

var ab1 = new ABad([2, 3, "5.78"]);
var ab2 = new ABad([2.5, 4.35, 4.77]);
var ab3 = new ABad([7, 8, 2]);
var ab4 = new ABad([ab1, ab2, ab3]);

Console.WriteLine(a1);
Console.WriteLine(a2);
Console.WriteLine(a3);
Console.WriteLine(a4);

Console.WriteLine(ab1);
Console.WriteLine(ab2);
Console.WriteLine(ab3);
Console.WriteLine(ab4);

var sum = 0;
for (int i = 0; i < 3; i++)
{
    sum += a1[i];
}

var sum2 = 0;
for (int i = 0; i < 3; i++)
{
    sum2 += (int)ab1[i];
}

class A<T>
    where T : struct, IComparable
{
    T []arr;

    public A(T [] mas)
    {
        arr = (T[]) mas.Clone();
    }

    public T this[int i] => arr[i];

    public override string ToString()
    {
        return "[" + string.Join ("; ", arr) + "]";
    }
}

class ABad
{
    object[] arr;

    public ABad(object[] mas)
    {
        arr = (object[])mas.Clone();
    }

    public object this[int i] => arr[i];

    public override string ToString()
    {
        return "[" + string.Join("; ", arr) + "]";
    }
}
```

## Разбор по блокам

### Блок 1. Создание `A<T>`

Создаются объекты `A<int>` и `A<double>`. Это один класс, но с разными типами параметра `T`.

### Блок 2. Создание `ABad`

`ABad` принимает массив `object[]`, поэтому в одном массиве могут оказаться числа и строка.

### Блок 3. Вывод

`Console.WriteLine` вызывает переопределенный `ToString`.

### Блок 4. Сумма через `A<int>`

```csharp
sum += a1[i];
```

Индексатор возвращает `int`, приведение не нужно.

### Блок 5. Сумма через `ABad`

```csharp
sum2 += (int)ab1[i];
```

Индексатор возвращает `object`, поэтому нужно явное приведение.

## Связи

- Использует: [[Класс — A<T>]], [[Класс — ABad]].
- Демонстрирует: generics, индексаторы, ограничения типа.

## Что нужно уметь объяснить преподавателю

- Что такое `T`.
- Что делает `where T : struct, IComparable`.
- Почему `A<T>` безопаснее, чем `ABad`.
- Почему в `ABad` появляется явное приведение.

