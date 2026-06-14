# ChebyshevNodes.cs

## Путь

`Lection-Abstract/ChebyshevNodes.cs`

## Назначение

Файл содержит класс [[Класс — ChebyshevNodes]].

## Исходный код

```csharp
﻿namespace Lection_Abstract
{
    public class ChebyshevNodes : Nodes
    {
        public ChebyshevNodes(double a, double b, int n): base(a, b, n) { }
        public ChebyshevNodes(int n) : base(n) { }

        public override double this[int index] => 
            (Left+Right)/2.0 + 0.5*(Right-Left)*Math.Cos((2.0*(Count - index) - 1.0)/(2.0*(Count))*Math.PI);
    }
}
```

## Разбор

Класс переопределяет индексатор и возвращает узлы по формуле с косинусом.

