# Класс — ChebyshevNodes

## Исходный файл

`Lection-Abstract/ChebyshevNodes.cs`

## Назначение класса

`ChebyshevNodes` возвращает узлы Чебышева на отрезке.

## Наследование

```csharp
public class ChebyshevNodes : Nodes
```

Класс наследуется от [[Класс — Nodes]].

## Конструкторы

```csharp
public ChebyshevNodes(double a, double b, int n): base(a, b, n) { }
public ChebyshevNodes(int n) : base(n) { }
```

## Индексатор

```csharp
public override double this[int index] => 
    (Left+Right)/2.0 + 0.5*(Right-Left)*Math.Cos((2.0*(Count - index) - 1.0)/(2.0*(Count))*Math.PI);
```

Индексатор возвращает узел по формуле с `Math.Cos`.

## Что сказать на экзамене

Класс показывает, что наследники могут иметь одинаковый внешний интерфейс, но разную внутреннюю формулу вычисления.

