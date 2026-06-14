# Program.cs

## Путь

`TaskTest/Program.cs`

## Назначение

Файл запускает три способа подсчета простых чисел и измеряет время.

## Исходный код

```csharp
﻿using System.Diagnostics;
using TaskTest;

var ppc = new ParallelTaskCounter(0, 1_000_000);
var sw = new Stopwatch();
sw.Start();
var result = await ppc.GetPrimeCount();
sw.Stop();
Console.WriteLine($"{result} by {sw.ElapsedMilliseconds}мс.");

var ptc = new ParallelThreadCounter(0, 1_000_000);
sw.Restart();
result = ptc.Start();
sw.Stop();
Console.WriteLine($"{result} by {sw.ElapsedMilliseconds}мс.");

//sw.Restart();
//result = 0;
//var locker = new object();
//var start = 0;
//var end = 1_000_000;
//Parallel.ForEach(Partitioner.Create(start, end + 1,
//                  rangeSize: Math.Max(1, (end - start + 1) / (Environment.ProcessorCount * 100))),
//    range =>
//    {
//        var localCount = 0;
//        for (int i = range.Item1; i < range.Item2; i++)
//        {
//            if (IsPrime(i)) localCount++;
//        }
//        lock (locker) result += localCount;
//    });
//sw.Stop();
//Console.WriteLine($"{result} by {sw.ElapsedMilliseconds}мс.");

result = 0;
var locker = new object();
var start = 0;
var end = 1_000_000;
sw.Restart();
Parallel.For(start, end + 1, i =>
{
    if (IsPrime(i))
    {
        lock (locker) result++;
    }
});
sw.Stop();
Console.WriteLine($"{result} by {sw.ElapsedMilliseconds}мс.");

bool IsPrime(int value)
{
    if (value <= 1) return false;
    for (int i = 2; i < value; i++)
    {
        if (value % i == 0) return false;
    }
    return true;
}
```

## Разбор

Сначала используется `ParallelTaskCounter`, затем `ParallelThreadCounter`, затем `Parallel.For`.

Top-level `await` используется в строке:

```csharp
var result = await ppc.GetPrimeCount();
```

## Что нужно уметь объяснить преподавателю

- чем `Task` отличается от `Thread`;
- зачем нужен `await`;
- зачем нужен `lock`;
- почему локальный результат лучше общего счетчика.

