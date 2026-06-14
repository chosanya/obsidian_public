# ParallelTaskCounter.cs

## Путь

`TaskTest/ParallelTaskCounter.cs`

## Назначение

Файл содержит класс [[Класс — ParallelTaskCounter]].

## Исходный код

```csharp
﻿using System;
using System.Collections.Generic;
using System.Text;

namespace TaskTest
{
    public class ParallelTaskCounter
    {

        private int _start;
        private int _end;
        public ParallelTaskCounter(int start, int end)
        {
            _start = start;
            _end = end;
        }

        public async Task<int> GetPrimeCount()
        {
            var parts = Environment.ProcessorCount * 10000;
            var fullSize = _end - _start + 1;
            if (fullSize <= 0) return 0;

            var partSize = Math.Max(1, fullSize / parts);
            var tasks = new List<Task<int>>();
            for (int i = _start; i <= _end; i += partSize)
            {
                var start = i;
                var end = Math.Min(_end, i + partSize - 1);
                tasks.Add(CountPrimesInRange(start, end));
            }
            var results = await Task.WhenAll(tasks);
            var result = results.Sum();
            return result;
        }

        private bool IsPrime(int value)
        {
            if (value <= 1) return false;
            for (int i = 2; i < value; i++)
            {
                if (value % i == 0) return false;
            }
            return true;
        }

        private Task<int> CountPrimesInRange(int start, int end)
        {
            return Task.Run(() =>
            {
                var count = 0;
                for (int i = start; i <= end; i++)
                {
                    if (IsPrime(i)) count++;
                }
                return count;
            });
        }
    }
}
```

## Разбор

Класс создает много задач, каждая считает свой диапазон и возвращает число простых чисел.

