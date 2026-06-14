# RandomNodes.cs

## Путь

`Lection-Abstract/RandomNodes.cs`

## Назначение

Файл содержит класс [[Класс — RandomNodes]].

## Исходный код

```csharp
﻿using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Lection_Abstract
{
    public class RandomNodes : Nodes
    {
        private Random r = new Random();
        private double[] _nodes;
        public override double this[int index] => _nodes[index];

        public RandomNodes(double a, double b, int n) : base(a, b, n) {
            _nodes = new double[n];
            for (int i = 0; i < n; i++)
            {
                _nodes[i] = r.NextDouble() * (b - a) + a;
            }
            Array.Sort(_nodes);
        }
        public RandomNodes(int n) : this(0.0, 1.0, n) { }
    }
}
```

## Разбор

Класс заранее создает массив случайных узлов, сортирует его и возвращает элементы по индексу.

