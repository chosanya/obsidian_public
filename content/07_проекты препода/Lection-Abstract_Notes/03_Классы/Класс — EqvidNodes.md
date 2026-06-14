# Класс — EqvidNodes

## Исходный файл

`Lection-Abstract/EqvidNodes.cs`

## Назначение класса

`EqvidNodes` возвращает равномерно расположенные узлы на отрезке.

## Наследование

```csharp
public class EqvidNodes : Nodes
```

Класс наследуется от [[Класс — Nodes]].

## Конструкторы

```csharp
public EqvidNodes(double a, double b, int n) : base(a, b, n) { }
public EqvidNodes(int n) : base(n) { }
```

Конструкторы вызывают конструкторы базового класса.

## Индексатор

```csharp
public override double this[int index]
{
    get => (Right - Left) / (Count - 1) * index + Left;
}
```

Возвращает равномерный узел по формуле.

## Что сказать на экзамене

`EqvidNodes` переопределяет абстрактный индексатор и тем самым реализует конкретный способ построения узлов.

