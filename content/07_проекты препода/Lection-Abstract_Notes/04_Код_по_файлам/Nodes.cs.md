# Nodes.cs

## Путь

`Lection-Abstract/Nodes.cs`

## Назначение

Файл содержит абстрактный базовый класс [[Класс — Nodes]].

## Исходный код

```csharp
﻿using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Lection_Abstract
{
    public abstract class Nodes
    {
        double _left;
        double _right;
        int _count;

        public double Left => _left;
        public double Right => _right;
        public int Count => _count;

        public Nodes(double a, double b, int n) {
            _left = a;
            _right = b;
            _count = n;
        }

        public Nodes(int n) : this(0.0, 1.0, n) { }
        
        public abstract double this[int index] { get; }

        // public abstract double GetNode(int index);


    }
}
```

## Разбор

Класс хранит общие данные для всех видов узлов и объявляет абстрактный индексатор. Наследники обязаны реализовать этот индексатор.

