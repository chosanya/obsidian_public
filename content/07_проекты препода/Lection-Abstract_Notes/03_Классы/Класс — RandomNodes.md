# Класс — RandomNodes

## Исходный файл

`Lection-Abstract/RandomNodes.cs`

## Назначение класса

`RandomNodes` создает случайные узлы на отрезке и сортирует их.

## Поля

```csharp
private Random r = new Random();
private double[] _nodes;
```

`r` нужен для генерации случайных чисел, `_nodes` хранит массив узлов.

## Наследование

```csharp
public class RandomNodes : Nodes
```

Класс наследуется от [[Класс — Nodes]].

## Индексатор

```csharp
public override double this[int index] => _nodes[index];
```

Возвращает заранее созданный случайный узел.

## Конструкторы

```csharp
public RandomNodes(double a, double b, int n) : base(a, b, n)
```

Создает массив, заполняет его случайными значениями и сортирует.

```csharp
public RandomNodes(int n) : this(0.0, 1.0, n) { }
```

## Что сказать на экзамене

`RandomNodes` отличается от других наследников тем, что не вычисляет узел каждый раз по формуле, а заранее создает массив узлов и возвращает элементы из него.

