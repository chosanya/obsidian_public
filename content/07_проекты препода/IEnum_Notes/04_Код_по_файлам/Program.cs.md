# Program.cs

## Путь

`IEnum/Program.cs`

## Назначение

Файл содержит демонстрацию `IReadOnlyCollection<double>`, `yield return`, `enum` и индексатора.

## Исходный код

```csharp
﻿using System.Collections;
using System.Diagnostics;

var eqNodes = new Nodes(-1, 1, 5, NodesType.Equidistant);
foreach (var node in eqNodes)
{
    Console.WriteLine(node);
}

Console.WriteLine(eqNodes[3]);

public enum NodesType{
    Equidistant, Chebyshev, Random
}

public class Nodes : IReadOnlyCollection<double>
{
    double _left;
    double _right;
    int _count;
    NodesType _type;
    public int Count => _count;

    public Nodes(double left, double right, int count, NodesType type)
    {
        if(left >= right)
        {
            throw new ArgumentException("Левый конец должен быть меньше правого");
        }
        if(count <= 1)
        {
            throw new ArgumentException("Узлов должно быть больше");
        }
        _left = left;
        _right = right;
        _count = count;
        _type = type;
    } 

    public IEnumerator<double> GetEnumerator()
    {
        switch (_type)
        {
            case NodesType.Equidistant:
            {
                    var distance = (_right - _left) / (_count - 1);
                    for (int i = 0; i < _count; i++)
                    {
                        yield return _left + distance * i;
                    }
                    break;
            }
            case NodesType.Chebyshev:
            {

                    break;
            }
            case NodesType.Random:
            {

                    break;   
            }
        }
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }

    public double this[int index]
    {
        get
        {
            var i = 0;
            if (index < 0 || index >= _count)
            {
                throw new ArgumentException("Указан неверный индекс");
            } 
            foreach(var elem in this)
            {
                if (i++ == index) return elem;
            }
            return Double.NaN;
        }
    }
}
```

## Разбор по блокам

### Блок 1. Создание и обход узлов

Создается `Nodes` с типом `Equidistant`, затем узлы выводятся через `foreach`.

### Блок 2. Индексатор

`eqNodes[3]` возвращает четвертый узел.

### Блок 3. `NodesType`

Перечисление задает способ построения узлов.

### Блок 4. `Nodes`

Класс реализует `IReadOnlyCollection<double>`, проверяет параметры, выдает узлы через `yield return` и поддерживает доступ по индексу.

## Что нужно уметь объяснить преподавателю

- Что такое `IReadOnlyCollection`.
- Как `foreach` связан с `GetEnumerator`.
- Как работает индексатор.
- Почему в конструкторе есть проверки.
- Почему `Chebyshev` и `Random` сейчас не дают значений.

