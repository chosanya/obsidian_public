# Program.cs

## Путь

`Enumarations/Program.cs`

## Назначение

Файл содержит демонстрацию `foreach`, `IEnumerable<T>`, `IEnumerator<T>` и `yield return`.

## Исходный код

```csharp
﻿using System.Collections;
using Lesson;

var f = new Fibo();
foreach (var value in f)
{
    Console.WriteLine(value);
}
var p = new PrimeNum ();
foreach (var value in p)
{
    Console.WriteLine(value);
}

namespace Lesson
{
    class Fibo : IEnumerable<int>
    {
        public IEnumerator<int> GetEnumerator()
        {
            int a = 0, b = 1;
            yield return a;
            yield return b;
            for (int i = 0; i <= 7; i++) {
                b = a + b;
                a = b - a;
                yield return b;
            }
            
        }


        IEnumerator IEnumerable.GetEnumerator()
        {
            return GetEnumerator();
        }
    }

    class Odd : IEnumerable<int>
    {
        private IEnumerator<int> _oddEnumerator = new OddEnumerator(3, 20);
        public IEnumerator<int> GetEnumerator()
        {
            return _oddEnumerator;
        }

        IEnumerator IEnumerable.GetEnumerator()
        {
            return GetEnumerator();
        }
    }

    class OddEnumerator : IEnumerator<int>
    {
        private int _min;
        private int _max;
        private int _current;
        public OddEnumerator(int min, int max)
        {
            _min = min + (min % 2 == 0? 1: 0);
            _max = max - (1 - max % 2);
            _current = _min - 2;
        }
        public int Current => _current;

        object IEnumerator.Current => Current;

        public void Dispose()
        {
            Reset();
        }

        public bool MoveNext()
        {
            _current += 2;
            return _current < _max;
        }

        public void Reset()
        {
            _current = _min - 2;
        }
    }


}
class PrimeNum : IEnumerable<int>
{
    public IEnumerator<int> GetEnumerator()
    {
        for (int i = 2; i < 100; i++)
        {
            if (IsPrime(i)) yield return i;
        }
    }
    private bool IsPrime(int a)
    {
        for ( int i = 2; i * i <= a; i++)
        {

            if (a % i == 0) return false;
           
        }
        return true;
    }
    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }
}
```

## Разбор по блокам

### Блок 1. Обход `Fibo`

Создается объект `Fibo`, затем `foreach` выводит его значения. Это возможно, потому что `Fibo` реализует `IEnumerable<int>`.

### Блок 2. Обход `PrimeNum`

Создается объект `PrimeNum`, затем `foreach` выводит простые числа.

### Блок 3. `Fibo`

`Fibo` использует `yield return`, поэтому код выглядит как обычный цикл, но на самом деле создает ленивую последовательность.

### Блок 4. `Odd` и `OddEnumerator`

`Odd` возвращает объект `OddEnumerator`. Это ручная реализация механизма, который `yield` обычно скрывает.

### Блок 5. `PrimeNum`

`PrimeNum` выдает числа только если `IsPrime` возвращает `true`.

## Связи

- Использует: [[Класс — Fibo]], [[Класс — PrimeNum]], [[Класс — Odd]], [[Класс — OddEnumerator]].
- Работает с: `IEnumerable<int>`, `IEnumerator<int>`.

## Что нужно уметь объяснить преподавателю

- Как `foreach` связан с `IEnumerable`.
- Чем `IEnumerable<T>` отличается от `IEnumerator<T>`.
- Что делает `yield return`.
- Почему `OddEnumerator` должен иметь `MoveNext` и `Current`.

