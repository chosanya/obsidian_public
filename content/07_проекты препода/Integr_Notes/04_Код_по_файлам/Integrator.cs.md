# Integrator.cs

## Путь

`Integr/Integrator.cs`

## Назначение

Файл содержит класс [[Класс — Integrator]].

## Исходный код

```csharp
﻿using System;
using System.Collections.Generic;
using System.Text;

namespace Integr
{
    public class Integrator
    {
        public double A { get; set; }
        public double B { get; set; }
        public int N { get; set; }
        public Integrator(double a=0.0, double b=1.0, int n=10) 
        {
            A = a;
            B = b;
            N = n;
        }

        public double F(double x)
        {
            return Math.Sin(x*x) + 5*Math.Cos(2*x)* Math.Cos(2*x); 
        }

        public double IntegrateByMidpointRule() 
        {
            double sum=0.0;
            double h = (B - A) / N;
            for (int i = 0; i < N; i++) {
                sum += F(h / 2 + A+i * h) * h;
            }
            return sum;
        }
    }
}
```

## Разбор

Класс хранит параметры интегрирования и выполняет вычисление. Метод средних прямоугольников берет середину каждого отрезка и суммирует `F(x) * h`.

