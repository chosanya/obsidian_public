# ParallelSummator.cs

## Путь

`Threads1/ParallelSummator.cs`

## Назначение

Файл содержит класс [[Класс — ParallelSummator]].

## Исходный код

```csharp
﻿using System;
using System.Collections.Generic;
using System.Text;

namespace Threads1
{
    public class ParallelSummator
    {
        private const int parts = 16;
        public int N
        {
            get => field;
            set => field = Math.Abs(value);
        }

        public long Result
        {
            get => field;
            private set => field = value;
        }

        public ParallelSummator(int n)
        {
            N = n;
        }

        private void CalcPartSum(object k)
        {
            int step = (int)k;
            for (int i = step + 1; i <= N; i += parts)
            {
                Result += i;
            }
        }

        public void CalcSum()
        {
            List<Thread> threads = new List<Thread>();
            for (int i = 0; i < parts; i++) { 
                threads.Add(new Thread(CalcPartSum));
                threads.Last().Start(i);
            }
            foreach (Thread thread in threads)
            {
                thread.Join();
            }
        }
    }
}
```

## Разбор

Класс запускает 16 потоков. Каждый поток получает свой номер и суммирует числа с шагом `parts`.

## Проблемное место

`Result += i` выполняется без синхронизации.

