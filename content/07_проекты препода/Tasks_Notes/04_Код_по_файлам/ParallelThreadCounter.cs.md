# ParallelThreadCounter.cs

## Путь

`TaskTest/ParallelThreadCounter.cs`

## Назначение

Файл содержит класс [[Класс — ParallelThreadCounter]].

## Исходный код

```csharp
﻿namespace TaskTest
{
    public class ParallelThreadCounter
    {
        private int _start;
        private int _end;
        
        public ParallelThreadCounter(int start, int end) {
            _start = start;
            _end = end;
        }

        public int Start()
        {
            var parts = Environment.ProcessorCount;
            var fullSize = _end - _start + 1;
            var partSize = fullSize / parts;
            var append = (fullSize % parts == 0) ? 0 : 1;
            var threads = new List<Thread>(parts + append);
            var result = 0;
            for (int i = 0; i < parts + append; i++)
            {
                var part = i;
                threads.Add(new Thread(() =>
                {
                    var count = 0;
                    var start = part * partSize;
                    var end = Math.Min(_end, (part + 1) * partSize - 1);
                    for (int i = start; i <= end; i++)
                    {
                        if (IsPrime(i)) count++;
                    }
                    lock (this)
                    {
                        result += count;
                    }
                }));
                threads.Last().Start();
            }
            foreach (var t in threads)
            {
                t.Join();
            }
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
    }
}
```

## Разбор

Класс создает потоки вручную и использует `lock`, чтобы безопасно прибавлять локальный результат к общему.

