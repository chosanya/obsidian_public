# Program.cs

## Путь

`Threads1/Program.cs`

## Назначение

Файл запускает последовательное и параллельное суммирование и измеряет время выполнения.

## Исходный код

```csharp
﻿using System.Diagnostics;
using Threads1;

var n = 2_000_000_000;
var sequentialSummator = new SequentialSummator(n);
var stopwatch = new Stopwatch();
stopwatch.Start();
sequentialSummator.CalcSum();
stopwatch.Stop();
Console.WriteLine("{0} за {1} мс.", sequentialSummator.Result, stopwatch.ElapsedMilliseconds);

var parallelSummator = new ParallelSummator(n);
stopwatch.Restart();
parallelSummator.CalcSum();
stopwatch.Stop();
Console.WriteLine("{0} за {1} мс.", parallelSummator.Result, stopwatch.ElapsedMilliseconds);
```

## Разбор

Сначала создается `SequentialSummator`, затем запускается `CalcSum`. После этого аналогично запускается `ParallelSummator`.

`Stopwatch` используется для измерения времени.

## Что нужно уметь объяснить преподавателю

- зачем нужна последовательная версия;
- как работает `Stopwatch`;
- почему параллельная версия может дать неправильный результат.

