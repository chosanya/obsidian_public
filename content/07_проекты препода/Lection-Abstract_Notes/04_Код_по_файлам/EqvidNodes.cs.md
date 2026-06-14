# EqvidNodes.cs

## Путь

`Lection-Abstract/EqvidNodes.cs`

## Назначение

Файл содержит класс [[Класс — EqvidNodes]].

## Исходный код

```csharp
﻿using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Lection_Abstract
{
    public class EqvidNodes : Nodes
    {
        public EqvidNodes(double a, double b, int n) : base(a, b, n) { }
        public EqvidNodes(int n) : base(n) { }
        public override double this[int index]
        {
            get => (Right - Left) / (Count - 1) * index + Left;
        }
    }
}
```

## Разбор

Класс наследуется от `Nodes` и переопределяет индексатор формулой равномерных узлов.

