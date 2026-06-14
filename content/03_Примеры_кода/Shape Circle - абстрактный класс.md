---
type: code-example
discipline: OOP
language: C#
tags:
  - пример-кода
---
# Shape Circle - абстрактный класс

> [!tip] Простыми словами: Пример показывает абстрактную общую фигуру и конкретный круг с расчётом площади.

#### Когда нужен абстрактный класс

Когда классы действительно являются родственными сущностями и имеют общее состояние или реализацию.

Например:
-- Animal → Dog, Cat; 
-- Shape → Circle, Rectangle; 
-- Employee → Manager, Programmer.

Можно вынести общее состояние:

```csharp
public abstract class Shape
{
    public string Name { get; set; }
    public abstract double CalculateArea();
    public void PrintName()
    {
        Console.WriteLine(Name);
    }
}
```

Производный класс:

```csharp
public class Circle : Shape
{
    public double Radius { get; set; }
    public override double CalculateArea()
    {
        return Math.PI * Radius * Radius;
    }
}
```
## Связи
- Связано с: [[Абстрактный класс]]
- Связано с: [[Абстрактный метод]]

## Источник
- файл: `5.tex`
- раздел: Когда нужен абстрактный класс
