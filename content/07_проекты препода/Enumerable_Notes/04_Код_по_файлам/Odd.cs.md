# Odd.cs

## Путь

`Enumerable/Odd.cs`

## Назначение

Файл содержит активный top-level код проекта и классы для перечисляемых последовательностей.

## Исходный код

```csharp
﻿using Enumerable;
using System.Collections;

var oddSequence = new Odd(0, 100);
foreach (var item in oddSequence)
{
    Console.Write($"{item} ");
    if (item > 10) break;
}
Console.WriteLine();
foreach (var item in oddSequence)
{
    Console.Write($"{item} ");
    if (item > 10) break;
}
Console.WriteLine();
var evenSequence = new Even(0, 100);
foreach (var item in evenSequence)
{
    Console.Write($"{item} ");
    if (item > 10) break;
}
Console.WriteLine();

var fibo = new Fibonacci();
foreach (var item in fibo)
{
    Console.Write($"{item} ");
}
Console.WriteLine();

foreach (var item in fibo)
{
    Console.Write($"{item} ");
}
Console.WriteLine();

namespace Enumerable
{
    public class Fibonacci : IEnumerable<long>
    {
        public IEnumerator<long> GetEnumerator()
        {
            var a = 0;
            var b = 1;
            //yield return a;
            yield return b;
            while (b > 0)
            {
                b += a;
                a = b - a;
                if (b < 0) yield break;
                yield return b;
            }
        }

        IEnumerator IEnumerable.GetEnumerator()
        {
            return GetEnumerator();
        }
    }
    public class Even : IEnumerable<int>
    {
        private int _minValue;
        private int _maxValue;
        public Even(int minValue, int maxValue) {
            if (minValue >= maxValue) throw new ArgumentException("Границы диапазона заданы неверно");
            _minValue = minValue + minValue % 2;
            _maxValue = maxValue - maxValue % 2;
        }

        public IEnumerator<int> GetEnumerator()
        {
            for (int current = _minValue; current <= _maxValue; current+=2)
            {
                yield return current;
            }
        }

        IEnumerator IEnumerable.GetEnumerator()
        {
            return GetEnumerator();
        }
    }

    public class Odd : IEnumerable<int>
    {
        private OddEnumerator enumerator;
        public Odd(int minValue, int maxValue) {
            enumerator = new OddEnumerator(minValue, maxValue);
        }
        public IEnumerator<int> GetEnumerator()
        {
            return enumerator;
        }

        IEnumerator IEnumerable.GetEnumerator()
        {
            return GetEnumerator();
        }
    }

    class OddEnumerator : IEnumerator<int>
    {
        private int _current;
        private int _minValue;
        private int _maxValue;
        public int Current => _current;

        object IEnumerator.Current => Current;

        public OddEnumerator(int minValue, int maxValue)
        {
            if (minValue >= maxValue) throw new ArgumentException("Границы диапазона заданы неверно");
            _minValue = minValue + (1 - minValue % 2);
            _maxValue = maxValue - (1 - maxValue % 2);
            Reset();
        }

        public void Dispose()
        {
            Reset();
        }

        public bool MoveNext()
        {
            _current += 2;
            return _current <= _maxValue;
        }

        public void Reset()
        {
            _current = _minValue - 2;
        }
    }
}
```

## Разбор по блокам

### Блок 1. Повторный обход `Odd`

Два раза выполняется `foreach` по одному объекту `oddSequence`. Это демонстрирует проблему состояния ручного перечислителя.

### Блок 2. Обход `Even`

`Even` использует `yield return`, поэтому обход получается проще.

### Блок 3. Повторный обход `Fibonacci`

`Fibonacci` тоже использует `yield`, поэтому повторный обход снова начинается сначала.

### Блок 4. Классы последовательностей

Внутри namespace `Enumerable` объявлены классы `Fibonacci`, `Even`, `Odd`, `OddEnumerator`.

## Что нужно уметь объяснить преподавателю

- Почему `foreach` работает с этими классами.
- Что такое `IEnumerable<T>`.
- Что такое `IEnumerator<T>`.
- Чем `yield return` отличается от ручного перечислителя.
- Зачем нужен `yield break`.

